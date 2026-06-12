---
title: "What is best USB wireless card for Ubuntu 11.10?"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by frank cox on 2012-01-07
What is best USB wireless card for Ubuntu 11.10?
I tried using a Belkin n300 but no luck. 
Am I better of with PCI card?

Is there a site wit a list of Linux compatible hardware??

TIA!

---

### Post by deonis on 2012-01-07
The one I bought recently was TP-Link TL-WN727N which worked as expected on Ubuntu 12.04 and 11.10 and it was something like 12 $

---

### Post by frank cox on 2012-01-17
Thanks

---

### Post by deonis on 2012-01-17
you are welcome :)

---

### Post by mogators on 2012-02-01
> **deonis said:**
> The one I bought recently was TP-Link TL-WN727N which worked as expected on Ubuntu 12.04 and 11.10 and it was something like 12 $

Will this work with the live CD without modification?  It is not working for me.  I'm running 10.04 and may upgrade to 11.10 if it works, but so far it is not.

---

### Post by deonis on 2012-02-01
It does not work in 10.04 without tweaking, but it's fine in 11.10 and 12.04.

---

### Post by frank cox on 2012-02-02
Thanks Deonis:

  It worked beautifully in 11.04 !

---

### Post by deonis on 2012-02-02
your are welcome :D

---

### Post by mogators on 2012-02-02
I just installed 11.10 on a test computer and still can't get mine working.  I have two of them, one is working on a WinXP computer, the other is for a Ubuntu box.  Have tried both of them in the test 11.10 machine and can't seem to see any network.  Is there anything I'm supposed to do to have this recognized?

---

### Post by deonis on 2012-02-02
did you try to see if its in ifconfig ? Try "ifconfig" in terminal it should display the interface for it if everything is fine. Also, are you sure that you're using the same  wificard as specified above?

---

### Post by mogators on 2012-02-02
> **deonis said:**
> did you try to see if its in ifconfig ? Try "ifconfig" in terminal it should display the interface for it if everything is fine. Also, are you sure that you're using the same  wificard as specified above?

ifconfig doesn't list any wireless device and iwconfig says no wireless extensions.

lsusb list Ralink Technology, Corp.

Device is tp-link tl-wn727n.

---

### Post by deonis on 2012-02-02
Something has to be wrong with your hardware. Did you try to put it in some other USB port ? It works fine on 11.10! What is your kernel version? type uname -r in terminal

---

### Post by mogators on 2012-02-02
Kernel is 3.0.0-12-generic.  I thought maybe this one adapter could be bad, but I tried the other one that is working fine in WinXP and get the same result.  Yes I have also tried changing usb ports.

---

### Post by deonis on 2012-02-02
the one I have is 3.0.0-15-generic try to update ...

---

### Post by mogators on 2012-02-02
Grabbing spare cat5 cable.  Installing updates.

The big question is, will I have any problems installing XBMC on this version of Ubuntu?  The computer I'm trying to get this wireless card working in is for my media center pc in the bedroom.  Was working with 10.04 and a cheapy G adapter, but I wanted better speeds.

For just downloading this yesterday, there sure are a lot of updates.  Almost done now.

---

### Post by mogators on 2012-02-02
Bangs head on desk, it is still not working.  May try installing Ndiswrapper and use the windows drivers.  Done with this for tonight though.  If anyone has any ideas, let me know.

---

### Post by deonis on 2012-02-03
Make sure you do not plug it in a USB hub. Best is to try a couple of USB ports at the back of your desktop tower. Do you have Windows on the computer you're trying to install the wifi adapter?

---

### Post by frank cox on 2012-02-03
Hve you tried Gnome-PPP ? Try it with sudo first. If it is not already installed it is local repository.in

---

### Post by mogators on 2012-02-03
I do have windows as a duel boot. I installed the adapter on it and it worked fine. The adapter is plugged directly into a port in the back of the machine. I have not tried gnome ppp yet.

---

### Post by frank cox on 2012-02-04
Are you trying to install the card to a LiveCd ? If so that is the problem. Install the program and update it.
It should install with no effort on your part at all. Plug and play .

---

### Post by mogators on 2012-02-04
No, I did a full install of 11.10 and after it did not work with my wireless, I hooked it up via ethernet and applied all updates to the system.  It still does not see any wifi networks.  Device is working fine if I boot into windows partition.

---

### Post by frank cox on 2012-02-05
Which wireless card did you use?

---

### Post by mogators on 2012-02-05
The one this entire thread is discussing, the TP-Link TL-WN727N.  I'm pretty much about to give up on it or Ubuntu for this machine.  I have several copies of Windows XP laying around that have been upgraded by Windows 7.  That way I know I won't have any issues getting XBMC installed as well.  I really like using Linux when I can but this is becoming a headache I don't need.

---

### Post by frank cox on 2012-02-05
I understand the frustration, dial-up can be a problem like that as well. It must be somethong simple as it worked on mine automatically.
The best advice I ever got here was from this guy: [david_kt]("http://ubuntuforums.org/member.php?u=187249")

I have a friend who is the IT guy for the local hospital and is a Ubuntu buff, will talk to him tommorrow

It is probably staring you in the face, What else have you hooked up to USB under Linux on the machine?

Check this out    "  [http://www.nirsoft.net/utils/usb_devices_view.html](http://www.nirsoft.net/utils/usb_devices_view.html) "
 
Run these with sudo 
 # lsusb 
# lspci
# dmidecode
# hardinfo

Hope it helps.

Last ditch effort is run windows in virtual box or install wubi

---

### Post by mogators on 2012-02-08
> **frank cox said:**
> I understand the frustration, dial-up can be a problem like that as well. It must be somethong simple as it worked on mine automatically.
The best advice I ever got here was from this guy: [david_kt]("http://ubuntuforums.org/member.php?u=187249")

I have a friend who is the IT guy for the local hospital and is a Ubuntu buff, will talk to him tommorrow

It is probably staring you in the face, What else have you hooked up to USB under Linux on the machine?

Check this out    "  [http://www.nirsoft.net/utils/usb_devices_view.html](http://www.nirsoft.net/utils/usb_devices_view.html) "
 
Run these with sudo 
 # lsusb 
# lspci
# dmidecode
# hardinfo

Hope it helps.

Last ditch effort is run windows in virtual box or install wubi

OK, here is the info for these except for hardinfo.  Wasn't sure how to put that info in here.  Looks like it sees the USB adapter but just doesn't seem to be recognizing it as a Network device.  By the way, since I'm running this on the computer in question, I have it hooked up via ethernet at the moment.

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. 

```

lspci
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

dmidecode
```
# dmidecode 2.9
SMBIOS 2.5 present.
44 structures occupying 1960 bytes.
Table at 0x000FB640.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 080015 
	Release Date: 08/03/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.15

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: BIOSTAR Group
	Product Name: G41-M7
	Version: ' '
	Serial Number: None
	UUID: 00020003-0004-0005-0006-000700080009
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: BIOSTAR Group
	Product Name: G41-M7
	Version: ' '
	Serial Number: None
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: BIOSTAR Group
	Type: Desktop
	Lock: Not Present
	Version: ' '
	Serial Number: None
	Asset Tag: None
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Pentium
	Manufacturer: Intel            
	ID: 7A 06 01 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 23, Stepping 10
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Celeron(R) CPU        E3300  @ 2.50GHz     
	Voltage: 1.3 V
	External Clock: 200 MHz
	Max Speed: 2500 MHz
	Current Speed: 2500 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 4-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 16384 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0009
		0x000A
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0 1
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 2 3
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 4 5
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: 6 7
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000D, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x000E, DMI type 15, 35 bytes
System Event Log
	Area Length: 4 bytes
	Header Start Offset: 0x0000
	Header Length: 2 bytes
	Data Start Offset: 0x0002
	Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
	Access Address: Index 0x046A, Data 0x046C
	Status: Invalid, Not Full
	Change Token: 0x00000000
	Header Format: No Header
	Supported Log Type Descriptors: 6
	Descriptor 1: End of log
	Data Format 1: OEM-specific
	Descriptor 2: End of log
	Data Format 2: OEM-specific
	Descriptor 3: End of log
	Data Format 3: OEM-specific
	Descriptor 4: End of log
	Data Format 4: OEM-specific
	Descriptor 5: End of log
	Data Format 5: OEM-specific
	Descriptor 6: End of log
	Data Format 6: OEM-specific

Handle 0x000F, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: 0x0010
	Number Of Devices: 4

Handle 0x0010, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0011, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x000F
	Partition Width: 0

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000F
	Error Information Handle: 0x0013
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer00
	Serial Number: SerNum00
	Asset Tag: AssetTagNum0
	Part Number: ModulePartNumber00

Handle 0x0013, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0014, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0012
	Memory Array Mapped Address Handle: 0x0011
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0015, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000F
	Error Information Handle: 0x0016
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer01
	Serial Number: SerNum01
	Asset Tag: AssetTagNum1
	Part Number: ModulePartNumber01

Handle 0x0016, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0017, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0015
	Memory Array Mapped Address Handle: 0x0011
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0018, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000F
	Error Information Handle: 0x0019
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer02
	Serial Number: SerNum02
	Asset Tag: AssetTagNum2
	Part Number: ModulePartNumber02

Handle 0x0019, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x001A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0018
	Memory Array Mapped Address Handle: 0x0011
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000F
	Error Information Handle: 0x001C
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer03
	Serial Number: SerNum03
	Asset Tag: AssetTagNum3
	Part Number: ModulePartNumber03

Handle 0x001C, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: Bad Read
	Granularity: Device Level
	Operation: Read
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x001B
	Memory Array Mapped Address Handle: 0x0011
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x001E, DMI type 22, 26 bytes
Portable Battery
	Location: Left side of System
	Manufacturer: Nikon Battery
	Manufacture Date: 08/11/97
	Serial Number: NI00123
	Name: Nikon Ultra Plus
	Chemistry: Nickel Cadmium
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: SMART Ver 0123
	Maximum Error: Unknown
	OEM-specific Information: 0x00000000

Handle 0x001F, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0020, DMI type 34, 11 bytes
Management Device
	Description: LM78-1
	Type: LM78
	Address: 0x00000000
	Address Type: I/O Port

Handle 0x0021, DMI type 28, 22 bytes
Temperature Probe
	Description: LM78A
	Location: Unknown
	Status: Unknown
	Maximum Value: Unknown
	Minimum Value Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Handle 0x0022, DMI type 36, 16 bytes
Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Handle 0x0023, DMI type 35, 11 bytes
Management Device Component
	Description: To Be Filled By O.E.M.
	Management Device Handle: 0x0020
	Component Handle: 0x0020
	Threshold Handle: 0x0021

Handle 0x0024, DMI type 27, 14 bytes
Cooling Device
	Temperature Probe Handle: 0x0021
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating

Handle 0x0025, DMI type 36, 16 bytes
Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Handle 0x0026, DMI type 35, 11 bytes
Management Device Component
	Description: To Be Filled By O.E.M.
	Management Device Handle: 0x0020
	Component Handle: 0x0023
	Threshold Handle: 0x0024

Handle 0x0027, DMI type 27, 14 bytes
Cooling Device
	Temperature Probe Handle: 0x0021
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating

Handle 0x0028, DMI type 36, 16 bytes
Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Handle 0x0029, DMI type 35, 11 bytes
Management Device Component
	Description: To Be Filled By O.E.M.
	Management Device Handle: 0x0020
	Component Handle: 0x0026
	Threshold Handle: 0x0027

Handle 0x002A, DMI type 39, 22 bytes
System Power Supply
	Power Unit Group: 1
	Location: To Be Filled By O.E.M.
	Name: To Be Filled By O.E.M.
	Manufacturer: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Model Part Number: To Be Filled By O.E.M.
	Revision: To Be Filled By O.E.M.
	Max Power Capacity: Unknown
	Status: Not Present
	Type: <OUT OF SPEC>
	Input Voltage Range Switching: <OUT OF SPEC>
	Plugged: Yes
	Hot Replaceable: No
	Cooling Device Handle: 0x0024

Handle 0x002B, DMI type 127, 4 bytes
End Of Table

```

---

### Post by deonis on 2012-02-08
Everything looks good to me. I am still do not understand why it does not work. :confused: It works on four of my PC without any tweaking. Can l ask you a weird question, did you enable wifi in the network manager? Sorry for that question, I am clueless. Do you have a life USB of Ubuntu 12.04 or 11.10? Can you try to see if the adapter works on other computers...

---

### Post by mogators on 2012-02-09
I am running 11.10 now, but it didn't work from the live cd either.  Haven't tried 12.04 yet.  I originally tried it on my system running 10.4LTS as that is the HTPC that I bought the card for.  I just ordered an EDIMAX ew-7722IN PCI card from Newegg today, hopefully I will have better luck with a internal device.  I'm hoping I will get better signal with it as well since it has dual external antenas.  

I don't see anywhere in network manager to enable wireless.  With my older adapters, I could just click on the network icon in the upper right and select the wireless network.  The only thing there now is wired connections.

---

### Post by deonis on 2012-02-09
when you right mouse click on the network manager icon you should have an option to enable networking and enable wireless. Do you have at least an option to enable networking?

---

### Post by deonis on 2012-02-09
if wifi is disabled you won't be able to see the wlan0 interface  with ifconfig.

---

### Post by frank cox on 2012-02-09
> **deonis said:**
> Everything looks good to me. I am still do not understand why it does not work. :confused: It works on four of my PC without any tweaking. Can l ask you a weird question, did you enable wifi in the network manager? Sorry for that question, I am clueless. Do you have a life USB of Ubuntu 12.04 or 11.10? Can you try to see if the adapter works on other computers...

The Rallink driver is causing your problems , it only needs the  rt2870sta driver.


blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

Hope that does it .

BTW it is better to post large text files to a file sharing service and then just add a link to it.

---

### Post by deonis on 2012-02-09
The wifi adapter works as expected on several of my computers. Why would he need to blacklist something?

---

### Post by mogators on 2012-02-09
> **deonis said:**
> when you right mouse click on the network manager icon you should have an option to enable networking and enable wireless. Do you have at least an option to enable networking?

I only have enable networking and it is checked.

---

### Post by frank cox on 2012-02-09
I am pretty sure the reason you have no option is the Ralink driver .

---

### Post by mogators on 2012-02-09
> **frank cox said:**
> The Rallink driver is causing your problems , it only needs the  rt2870sta driver.


blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

Hope that does it .

BTW it is better to post large text files to a file sharing service and then just add a link to it.

When I do a lsmod, I do not see any rt2* modules loaded.

---

### Post by mogators on 2012-02-11
Well, I finally have wireless working.  :D  My EDIMAX EW-7722In arrived Friday and I was able to get it working in my test machine running 11.10 and later in my HTPC running 10.4LTS.  Thanks to everyone who tried helping with the TP-Link, I may try it again with the test machine.  Also, thanks to this [[COLOR="Red"]*thread *[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1806897&highlight=ew-7722")for the help with the EDIMAX.  Here is the rundown of what I did with the EW-7722.
11.10 - Downloaded the drivers from Ralink (DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz) and unzipped.  In the unzipped files, edited os/linux/config.mk: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. This was key as before I did this, I could not connect to my wireless.  The readme file that came with the download had other stuff to edit, but these two lines are the only ones I changed.
sudo su
make
make install
echo rt3562sta >> /etc/modules
exit

edit /etc/modprobe.d/blacklist.conf and added:
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

rebooted and had wireless!

For 10.4LTS:
Same as above but did not need to edit blacklist.conf.  I guess the rt2x00 module is not already in the 2.6 kernel.

Hopefully this will help someone else down the line.

---

### Post by frank cox on 2012-02-11
> **mogators said:**
> When I do a lsmod, I do not see any rt2* modules loaded.


Not sure why but the main problem people have had with that card is the rallink driver. Not sure why some do and some don't. It worked like a champ for me. One possibility is that Dell is Ubuntu friendly as they supply machines preloaded with it?

Anyway I am glad you are up and running.

---

### Post by mogators on 2012-02-11
Well, I played around with the TP-Link adapter again on my 11.10 machine and managed to get it working.  Not sure what did it though.  I noticed my blacklist had rt2800pci instead of rt2800usb, so I added that as well.  Before rebooting, I downloaded drivers from Ralink (2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2) and made the same modifications to the config.mk file as above.  Did a make, then make install.  I didn't know what to add to the /etc/modules file so just gave a reboot a shot.  Low and behold, I had wireless networks showing up!  I could even connect to mine.  :)
Still glad I got the EDIMAX adapter as well since it is rated for 300mbs instead of 150.  It seems to have better signal strength and connects at a higher rate.  I copied a file from my server and the transfer rates seemed to be about the same (4.5mb/sec).  When I was connected with ethernet, I was getting over 8 mb/sec.  I guess I'll keep the TP-link as a spare as it was only $10 at Microcenter.

---

### Post by frank cox on 2012-02-12
> **mogators said:**
> Well, I played around with the TP-Link adapter again on my 11.10 machine and managed to get it working.  Not sure what did it though.  I noticed my blacklist had rt2800pci instead of rt2800usb, so I added that as well.  Before rebooting, I downloaded drivers from Ralink (2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2) and made the same modifications to the config.mk file as above.  Did a make, then make install.  I didn't know what to add to the /etc/modules file so just gave a reboot a shot.  Low and behold, I had wireless networks showing up!  I could even connect to mine.  :)
Still glad I got the EDIMAX adapter as well since it is rated for 300mbs instead of 150.  It seems to have better signal strength and connects at a higher rate.  I copied a file from my server and the transfer rates seemed to be about the same (4.5mb/sec).  When I was connected with ethernet, I was getting over 8 mb/sec.  I guess I'll keep the TP-link as a spare as it was only $10 at Microcenter.

Cool
Do you go to the microcenter in Houston?

---

### Post by mogators on 2012-02-12
> **frank cox said:**
> Cool
Do you go to the microcenter in Houston?

No, I go to the one in St. Louis.  I try to buy stuff there if it is not way overpriced compared to online.

---

### Post by anymoose on 2012-03-20
HI! This is the definitive fix for Ubuntu 11.10 OS and
TP LINK TL-WN727N(V3) Wifi USB Adapter
 
Use this link (only) if kernel version is shown below;
Ubuntu 11.10
 
ls /lib/modules
 
3.0.0-12-generic
 
Web Link;
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)
 
Use user Chili555 post #2. Everything is done in post #2 ie no
files to download no compilation, no other changes. This fix
must be entered carefully; all spelling, spaces and capital/lc
letters *must* be correct. Worked for me after reboot. Test
your adapter with MS-Win XP with included utility on CD ahead 
of time, if possible.
 
Not sure if this will work in Ubuntu live filesystem on CD for
obvious reasons. Works when filesystem is on HD disk and
USB stick.
 
This fix will be better for beginners than compiling and
loading a new device driver. It will get them going.
 
Signed; Anymoose

---

### Post by bogan on 2012-03-20
Hi!,** anymoose**,

Thanks for Posting the link for Chilli555's solution to the problems with the Ralink 5370 adapter and the rt28xx drivers, including the TP LINK TL-WN727N(V3) Wifi USB Adapter referred to in this Thread:
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)


Chao!, **bogan**.

---

### Post by Lloydb39 on 2012-09-06
I have a Belkin 300 and it works fine in 11.10 for me...

---

