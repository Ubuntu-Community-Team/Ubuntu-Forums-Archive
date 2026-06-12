---
title: "mythtv recording microphone sound"
date: 2009-05-30
forum: Multimedia Software
---

### Post by kidalabama on 2009-05-30
mythtv running very well but mythtv can't capture line in sound. mythtv capture mic  in sound. i plugged microphone in pink jack and plugged tv card sound patch cable to blue jack (line in jack). i can hear tv card sound and microphone captured sound. when speaking to microphone, myth tv capture my sound. and show 5 seconds delayed. 
I changed patch cable plugged to mic in (pink jack) but no sound captured and heared.

My Hardware 

tv card:aver tv analog card
sound: on board realtek alc662 sound card 
main board: D945GCLF 

```
# dmidecode 2.9
/dev/mem: Permission denied
nurettin@alp7:~$ sudo dmidecode 
# dmidecode 2.9
SMBIOS 2.4 present.
23 structures occupying 1121 bytes.
Table at 0x000E3590.

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U1PR
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel(R) Corporation
	ID: C2 06 01 00 FF FB E9 BF
	Version: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
	Voltage: 1.6 V
	External Clock: 133 MHz
	Max Speed: 4000 MHz
	Current Speed: 1600 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0002
	L2 Cache Handle: 0x0001
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative

Handle 0x0003, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: LF94510J.86A.0067.2008.0619.1959
	Release Date: 06/19/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 0.0
	Firmware Revision: 0.0

Handle 0x0004, DMI type 1, 27 bytes
System Information
	Manufacturer:                                 
	Product Name:                                 
	Version:                         
	Serial Number:                                 
	UUID: B32C8E98-742D-11DD-8934-0007E9BECBF3
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family: Not Specified

Handle 0x0005, DMI type 2, 20 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: D945GCLF
	Version: AAE27042-306
	Serial Number: AZLF834005BC
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0006
	Type: Unknown
	Contained Object Handles: 0

Handle 0x0006, DMI type 3, 17 bytes
Chassis Information
	Manufacturer:                                 
	Type: Unknown
	Lock: Not Present
	Version:                         
	Serial Number:                                 
	Asset Tag:                                 
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: ATX_PWR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000A, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI SLOT 1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 1
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x000B, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x000C, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Realtek RTL8102E Ethernet Device

Handle 0x000D, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) High Definition Audio Device

Handle 0x000E, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

Handle 0x000F, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0010, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 1

Handle 0x0011, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: J1MY
	Bank Locator: CHAN A DIMM 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 0x7F98000000000000
	Serial Number: 0x49CCA601
	Asset Tag: Unknown
	Part Number: 0x202020202020202020202020202020202020

Handle 0x0012, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0011
	Memory Array Mapped Address Handle: 0x0013
	Partition Row Position: 1

Handle 0x0013, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x0010
	Partition Width: 0

Handle 0x0014, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 14 00 11 00 03 9B 02

Handle 0x0015, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 15 00 5A 5A

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table

```

---

### Post by markackerman8@gmail.com on 2010-12-15
I am having the same problem, and once had it solved but forget how I solved it.  Anybody with any ideas?

Mark

---

