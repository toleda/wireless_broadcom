![alt text](https://github.com/toleda/wireless_half-mini/blob/master/wifi.jpeg)
# wireless_broadcom
**macOS Broadcom WiFi and Bluetooth**

WiFi and Bluetooth working out of box on macOS with Apple branded Broadcom BCM94360. Enables half mini and M.2 BCM4352 on High Sierra with method described below. Credit: RehabMan

**Updates**

1. 12/26/2017 - High Sierra Broadcom WiFi and Bluetooth Support

**Previous Repo:** https://github.com/toleda/airport_half_mini (Deprecated)

**Broadcom WiFi + BT**

1.    Half mini/BCM94360HMB/AzureWave AW-CB160H - Credit: Skvo, Post #758/[Guide] Airport - PCIe Half Mini v2
2.    PCIe/BCM94360CD/BCM9331CD native WiFi/ac and BT4LE (PCIe 1x, not HM)
3.    Half mini/BCM94352 HMB/AzureWave AW-CE123H/DW 1550 supports WiFi/ac and BT4LE
4.    M.2/BCM94352Z HMB/AzureWave AW-CE162NF/DW1560 supports WiFi/ac and BT4LE
5.    Half miniBCM943224 HMB supports WiFi and BT3

**User Responsibilities**

1.    Supported WiFi card sources - the usual
2.    WiFi and Bluetooth Antennas
3.    Mini PCIe to PCI/PCIe adapters (adapter must include motherboard USB connector for working BT)
4.    Clover_v4305 or newer

**Broadcom WiFi/Bluetooth Repo**

**Broadcom WiFi/Bluetooth Installation/10.13+**
Note: Requires AirPortBrcm4360.kext and BT4LE
⁃    AirPortBrcmNIC-MFG.kext - not applicable

**Step 1/Enable WiFi**

1.    README: https://github.com/RehabMan/OS-X-Fake-PCI-ID
2.    Download: https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/
3.    Install with kext installer to /System/Library/Extension:
        1.    FakePCIID.kext
        2.    FakePCIID_Broadcom_WiFi.kext

**Step 2/Enable BT**

1.    README: https://github.com/RehabMan/OS-X-BrcmPatchRAM
2.	Download: https://bitbucket.org/RehabMan/os-x-brcmpatchram/downloads/
3.	Install to EFI/CLOVER/kexts or kext installer to /System/Library/Extensions:
	1.	BrcmFirmwareRepo.kext
	2.	BrcmPatchRAM2.kext

**Step 3/Optional Features**

1.    Enable Handoff/Hot Spot (94352 only) - Credit: lisai9093
	⁃        Binary patch: IOBluetoothFamily
	    1.	    Find: 48 85 FF 74 47 48 8B 07
            2.     Replace: 41 BE 0F 00 00 00 EB 44
	⁃	Installation/Clover patch
	    1.	Download (View Raw):config-bcm94352-120.plist.zip
        2.	Paste patch to config.plist/KernelAndKextPatches/KextsToPatch
	⁃	BT4LE-Handoff-Hotspot
	2.




**Country Code**  (10.12/10.11/10.10 - all versions)

1. Country Code/Required
	2. 	Native: US/FCC (Hex: 55 53)
	2.	If not US/FCC, see Sebinouse, see #2 below
	3.	Special case, see [#a](https://www.tonymacx86.com/threads/guide-airport-pcie-half-mini-v2.104850/page-209), credit: jaymonkey, Post #2084
		1. Solves wake from sleep WiFi performance issue
3. ROW [Country Code](https://www.tonymacx86.com/threads/guide-airport-pcie-half-mini-v2.104850/page-209), credit: Sebinouse, Post #1159 (select one method)
	1. config-bcm94352...plist (see Repo)
		1. edit 5GHz-US/Replace/55 53 (US) to xx xx (CC)
		2. [ASCII/Hex/Base64](http://www.asciitohex.com)
	2. wireless_bcm94352...command (see Repo)
		1. CC prompt

**BCM94352 5 GHz/Handoff Patch (10.12+)**  
Credit: the-darkvoid 

1. Clover/kext patch
   1. Download [config-bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/config-bcm94352-120.plist.zip) (select View Raw)
	2. Paste 3 Patches to config.plist/KernelAndKextPatches/KextsToPatch

**BCM94352 5 GHz/Handoff Patch (10.11+)**  
Credit: Dokterdok, the-darkvoid, Sebinouse  
Select 1 or 2, not both

1. Kext/binary patch
   1. Download [wireless_bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/wireless_bcm94352-110-v4.0.command.zip) (select View Raw)
   2. Double click Downloads/wireless_bcm94352-...command
2. Clover/kext patch
   1. Download [config-bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/config-bcm94352-110.plist.zip) (select View Raw)
	1. Paste 3 Patches to config.plist/KernelAndKextPatches/KextsToPatch

**BCM94352 5 GHz/Handoff Patch (10.10+)**  
Credit: Dokterdok, the-darkvoid, Sebinouse  
Select 1 or 2, not both

1. Kext/binary patch
   1. Download [wireless_bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/wireless_bcm94352-100.command.zip) (select View Raw)
   2. Double click Downloads/wireless_bcm94352-...command
2. Clover/kext patch
   1. Download [config-bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/config-bcm94352-103.plist.zip) (select View Raw)
	1. Paste 3 Patches to config.plist/KernelAndKextPatches/KextsToPatch

**BCM94352 5 GHz Patch (10.9+)**  
Credit: Skvo  
Select 1 or 2, not both

1. Kext/binary patch
	1. Download [wireless_bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/wireless_bcm94352-90_patch.command.zip) (select View Raw)
   2. Double click Downloads/wireless_bcm94352-...command
   3. See Terminal Saved Output. . . (above)
2. Clover/kext patch
   1. Download [config-bcm94352-...](https://github.com/toleda/wireless_half-mini/blob/master/config-bcm94352-103.plist.zip) (select View Raw)
   2. Add 3 Patches to config.plist/KernelAndKextPatches/KextsToPatch

**Bluetooth 4LE (10.11+)**

1.	10.11 USB Issues/no BT
	1. Fix USB problem
2.	BT injection - RehabMan/OS-X-BrcmPatchRAM (2 kexts required)
	1.	REAMDME [BrcmPatchRAM -- RehabMan](https://github.com/RehabMan/OS-X-BrcmPatchRAM)
	2. Download [BrcmPatchRAM -- RehabMan](https://bitbucket.org/RehabMan/os-x-brcmpatchram/downloads)
	3. Install 2 kexts
		1.	BrcmFirmwareRepo.kext
		2.	BrcmPatchRAM2.kext
3.	Installation (a or b, not both)
	1.	Clover/Chameleon - use kext installer
		1.	System/Library/Extensions/
		2.	Library/Extensions/
4.	Working
	1.	Asus BCM94352 (0b05/17cf)
	2.	Azurewave CE-123H (13d3/3404)

**Bluetooth 4LE/4/3 (10.10+. 10.9+)**

1. REAMDME [BrcmPatchRAM -- RehabMan](https://github.com/RehabMan/OS-X-BrcmPatchRAM)
2. Download [BrcmPatchRAM -- RehabMan](https://bitbucket.org/RehabMan/os-x-brcmpatchram/downloads)
3.	BrcmPatchRAM.kext Installation (Select one method)
	1.	Clover/Chameleon - System/Library/Extensions/
		1.	use kext installer
	2.	Clover - EFI/CLOVER/kexts/10.10 or /10.9
4.	Working
	1.	Asus BCM94352 (0b05/17cf)
	2.	Azurewave CE-123H (13d3/3404

**Requirement** (+ all)

1.  OS X Versions (+ all)
    1.  10.11+/El Capitan 
    2.  10.10+/Yosemite
    3.  10.9+/Mavericks
    4.  10.8.5/Mountain Lion  
    Solution does not work, 10.8.4 or earlier
2. Boot Flags/Boot failure may result if ignored
	1. 10.11+/Disable SIP/set, restart, install, enable SIP, restart
		1. CLOVER/config.plist/RtVariables/
			1. BooterConfig/0x28
			2. CsrActiveConfig/0x3
		2. Chameleon - Extra/org.chameleon.Boot.plist
			1. CsrActiveConfig=3
	2. 10.10+/Allow unsigned kexts/set, restart, install
		1. Clover/config.plist/
			1. Boot/Arguments/kext-dev-mode=1
		2. Chameleon/Extra/org.chameleon.Boot.plist/
			1. Kernel Flags/kext-dev-mode=1

**Installation/Configuration/Troubleshooting**  
[Guide] airport_half-mini_details.pdf.zip (above)

**Tools**

1. [IOReg_v2.1](https://github.com/toleda/audio_ALCInjection/blob/master/IORegistryExplorer_v2.1.zip) (select View Raw)
2. [DPCIManger](http://sourceforge.net/projects/dpcimanager/)  
3. [MaciASL](http://sourceforge.net/projects/maciasl/)
4. Property List Editors -
	1. [Xcode](https://developer.apple.com/xcode/)  
	2. Property List Editor, PlistEdit Pro, TextEdit, etc.
	3. TextEdit, TextWrangler (last resort)
5. [Clover Configurator](http://www.osx86.net/files/file/49-clover-configurator/)
6. [Clover Wiki](http://clover-wiki.zetam.org/Home)

**Problem Reporting** (attach requested information)

1. Description of wireless problem
2. OS X version/motherboard model/BIOS version/processor/graphics
3. Procedure/Guide used
4. Copy of IOReg - IOReg_v2.1/File/Save a Copy As…, verify file (Tools 1.)
5.	Screenshots:
	1. DPCIManager/Status (Tools 2.)
	2. System Information/Hardware/Network/WiFi
	3. System Information/Hardware/Bluetooth
	4. System Information/Hardware/USB (Select Bluetooth 	device)
6.	DPCIManager/Misc/Boot Log
7.	MaciASL/File/Export Tableset As... (Tools 3.)
8.	Terminal/Shell/File/Export Text As. . . /wireless_bcm...command
9.	Chameleon
	1.	Extra/org.chameleon.Boot.plist
	2.	DPCIManager/Misc/Boot Log
	3.	Extra/dsdt.aml (if installed)
	4.	Extra/ssdt.aml (if installed)
10.	Clover
	1.	EFI/CLOVER/config.plist
	2.	DPCIManager/Misc/Boot Log
	3.	EFI/CLOVER/ACPI/Patched/dsdt.aml (if installed)
	4.	EFI/CLOVER/ACPI/Patched/ssdt.aml (if installed)
11.	Post to:
	1.	[Airport - InsanelyMac.com](http://www.insanelymac.com/forum/topic/292542-airport-pcie-half-mini/)
	2. [Airport - tonymacx86.com](http://www.tonymacx86.com/network/104850-guide-airport-pcie-half-mini-v2.html)

Credit  
THe KiNG   
Andy Vandijck  
PikeRAlpha  
Skvo  
Dokterdok  
the-darkvoid  
Sebinouse  

toleda
https://github.com/toleda/airport_half_mini
