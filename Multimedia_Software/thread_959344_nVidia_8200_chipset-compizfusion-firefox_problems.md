---
title: "nVidia 8200 chipset-compizfusion-firefox problems"
date: 2008-10-26
forum: Multimedia Software
---

### Post by fewjr on 2008-10-26
Hi All,
      My problem is that the nVidia driver I assume, is breaking webpages that I view in Firefox. Well here is what I have done so far. I installed 'Advanced Desktop Effects Settings'. I have the Cube running in CompizFusion. I installed Envy and used it to uninstall nVidia driver that came with Hardy....I think. It looks like it is still showing up in Administration>Hardware Drivers, but it says "not in use". I then let Envy install the driver it wanted to install (Automatic Hardware Detection). I am not sure after all that if my problem lies with the driver or Firefox or something else. The problem I encounter is that when I look at a webpage, say for example, A listing of a search in Google, as you go down the page the text starts to stack up on itself. Text seems to show up ontop of the next line and soforth. Thats the best way I can describe it.
     I thought I would give jwferks nVidia settings a try, the post is here, [http://ubuntuforums.org/showthread.php?t=886519](http://ubuntuforums.org/showthread.php?t=886519), page2, #20. I get as far as ```
sudo /etc/init.d/gdm stop
```. I get to the terminal session. Any commands I input doesn't show a response. Even if I do pwd, it doesn't show where I am. Anyway I continued by ```
cd /home/goblin/Desktop
```. then ```
sudo sh NV*
```. The install sequnce doesn't start. I get no output. Then i  did ```
sudo /etc/init.d/gdm start
```. Nothing happens here either, so I had to reboot. I went into Synaptic and checked for libc6-dev and it was already installed. So what do you think. The only way I can read webpages in Ubuntu is to use no extra visual effects. I really like the desktop cube, I find it very useful.I submitted here because I think it is nVidia 8200 problem Not sure. Your thoughts would be greatly appreciated.

Best Regards,
fewjr

---

### Post by fewjr on 2008-10-31
bump please.

---

### Post by fewjr on 2008-11-03
Anyone out there?

---

### Post by fewjr on 2008-11-07
bumping again!:)

---

### Post by GameKing505 on 2008-12-16
Same problem... 

I guess its a rare one since no one can help. Oh well, no cube for us...

---

### Post by fewjr on 2008-12-17
Well thats the thing....the cube works fine. I'm wondering if a different browser would work. Maybe its Firefox that has a problem with the effects.

---

### Post by fewjr on 2008-12-17
Hello All,
I know the folks here that answer our questions are helping out of the kindness of their hearts. Their time is valuable and much appreciated. I have a few unanswered post, but the one I need help with right now is this one: 
[http://ubuntuforums.org/showthread.php?p=6387125#post6387125](http://ubuntuforums.org/showthread.php?p=6387125#post6387125)
The Cube works fine and my nvidia drivers seem to work. I'm wondering if it is Firefox that has the problem with CompizFusion. Since the time I posted this problem I have switched to Intrepid Ibex in hopes of a fix, but it still does it. I cannot find anything on the problem since October. Here is a little info....anything else that would help please let me know.
```
goblin@goblin-lanbox:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
goblin@goblin-lanbox:~$ 

``` 
```
goblin@goblin-lanbox:~$ sudo dmidecode
[sudo] password for goblin: 
# dmidecode 2.9
SMBIOS 2.4 present.
34 structures occupying 1936 bytes.
Table at 0x000F0100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: F1
	Release Date: 04/22/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
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

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: M78SM-S2H
	Version:  
	Serial Number:  
	UUID: 30303146-4430-3542-3938-4434FFFFFFFF
	Wake-up Type: Power Switch
	SKU Number:  
	Family:  


Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: nVIDIA
	Product Name: M78SM-S2H
	Version:  
	Serial Number: OEM

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket M2
	Type: Central Processor
	Family: Athlon
	Manufacturer: AMD
	ID: B2 0F 06 00 FF FB 8B 17
	Signature: Family 15, Model 107, Stepping 2
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
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Hyper-threading technology)
	Version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
	Voltage: 1.1 V
	External Clock: 200 MHz
	Max Speed: 500 MHz
	Current Speed: 2600 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0008
	L2 Cache Handle: 0x0009
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 32 MB
	Maximum Total Memory Size: 64 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 2
		0x0006
		0x0007
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: 32 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	Current Speed: 32 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator:  
	External Connector Type: None
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator:  
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator:  
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM2
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: Other
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator: Detected
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 6
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 7
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0015, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x0016, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0017, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0016
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 800 MHz (1.2 ns)
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0018, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0016
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 800 MHz (1.2 ns)
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0019, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0016
	Partition Width: 32

Handle 0x001A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0017
	Memory Array Mapped Address Handle: 0x0019
	Partition Row Position: 1

Handle 0x001B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0018
	Memory Array Mapped Address Handle: 0x0019
	Partition Row Position: 1

Handle 0x001C, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x001D, DMI type 188, 244 bytes
OEM-specific Type
	Header and Data:
		BC F4 1D 00 00 00 00 E8 00 00 00 00 00 00 00 18
		01 00 00 00 01 06 76 00 00 00 00 00 03 00 00 00
		00 00 17 01 00 00 00 00 01 00 00 00 00 00 00 00
		02 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00
		04 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00
		06 00 00 00 00 00 00 00 07 00 00 00 01 18 00 E8
		40 00 10 0A 00 00 00 00 00 00 0F 00 EF 02 00 5D
		01 00 00 00 01 02 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		E0 3D F8 00 00 00 00 00 00 00 00 00 00 00 00 00
		46 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00
		24 CA 7E 5D 20 13 22 00 10 0C 01 00 6B 00 10 77
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x001E, DMI type 190, 212 bytes
OEM-specific Type
	Header and Data:
		BE D4 1E 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x001F, DMI type 192, 244 bytes
OEM-specific Type
	Header and Data:
		C0 F4 1F 00 16 15 15 16 15 15 14 15 16 00 00 00
		15 15 15 14 15 14 15 16 15 00 00 00 2B 00 00 00
		15 15 15 14 15 15 15 15 15 15 15 17 16 15 15 16
		15 15 2D 00 00 00 22 32 11 20 20 25 20 10 22 32
		11 20 20 25 20 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0020, DMI type 194, 244 bytes
OEM-specific Type
	Header and Data:
		C2 F4 20 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0021, DMI type 127, 4 bytes
End Of Table

goblin@goblin-lanbox:~$ 


```
```
goblin@goblin-lanbox:~$ sudo lshw
goblin-lanbox             
    description: Desktop Computer
    product: M78SM-S2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=30303146-4430-3542-3938-4434FFFFFFFF
  *-core
       description: Motherboard
       product: M78SM-S2H
       vendor: nVIDIA
       physical id: 0
       serial: OEM
       slot: &#65533;FDD
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F1 (04/22/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          slot: Socket M2
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP78S [GeForce 8200] LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom:0
             description: DVD reader
             product: DVD-ROM DDU1615
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: GYS5
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
        *-cdrom:1
             description: DVD writer
             product: DVD-RW  DVR-116D
             vendor: PIONEER
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 1.04
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-multimedia
          description: Audio device
          product: Realtek ALC1200 8-Channel High Definition Audio Codec
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-network DISABLED
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             logical name: wifi0
             version: 01
             serial: 00:15:e9:89:b4:1f
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
     *-ide:1
          description: IDE interface
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi2
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-disk:0
             description: ATA Disk
             product: Hitachi HDP72505
             vendor: Hitachi
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: GM4O
             serial: GEA530RE3AY2NE
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000e557f
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: df2e4001-7d5c-4cbe-81c1-61db62617ddf
                size: 59GiB
                capacity: 59GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-10-26 11:08:52 filesystem=ntfs label=Windows XP state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 406GiB
                capacity: 406GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 101MiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   logical name: /dev/.static/dev
                   capacity: 202GiB
                   configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 1027MiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 4094MiB
                   capabilities: nofs
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   capacity: 198GiB
        *-disk:1
             description: ATA Disk
             product: Hitachi HDP72505
             vendor: Hitachi
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: GM4O
             serial: GEB531RE36KS1F
             size: 465GiB (500GB)
             configuration: ansiversion=5 signature=000487cb
     *-network
          description: Ethernet interface
          product: MCP78S [GeForce 8200] Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:d0:5b:98:d4
          size: 1GB/s
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.107 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht bus_master cap_list
        *-display
             description: VGA compatible controller
             product: GeForce 8200
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: c
          bus info: usb@3:6
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE-A
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdc
             version: 9612
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE-A
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdd
             version: 9612
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE-A
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sde
             version: 9612
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE-A
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sdf
             version: 9612
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:c7:be:1d:9d:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
goblin@goblin-lanbox:~$ 


```
This is the version of Firefox:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4
 If anyone can guide me in this it would be great.

Thank You,
fewjr

---

### Post by overdrank on 2008-12-17
Please do not create multiple threads on the same issue. Threads merged and moved to  Multimedia & Video. :)

---

### Post by fewjr on 2008-12-17
Please explain....isn't this where you try to get help with unanswered post? I see that you merged my question here with the original thread., but how does this help?

---

### Post by overdrank on 2008-12-17
> **fewjr said:**
> Please explain....isn't this where you try to get help with unanswered post? I see that you merged my question here with the original thread., but how does this help?

Hi and I moved your last thread from the unanswered post teams page. The teams forum is not for support. I have merged it with your previous thread and move to a location I thought would be better to assist you.

---

### Post by fewjr on 2008-12-17
I apologize...I thought it was the place. It was the only place I saw relating to unanswered post. I posted somewhere before for unanswered post...can you tell me where that might have been? Maybe it was here then too...someone just took pitty on me;) 

Thanks

---

### Post by overdrank on 2008-12-17
> **fewjr said:**
> I apologize...I thought it was the place. It was the only place I saw relating to unanswered post. I posted somewhere before for unanswered post...can you tell me where that might have been? Maybe it was here then too...someone just took pitty on me;) 

Thanks

Hi and you originally posted in Hardware and laptops, this is why when I merged the thread I moved them also. :)
Edit I see you are using intrepid and have you tried using the newest driver from nvidia?

---

### Post by fewjr on 2008-12-17
Okay...I understand. Thanks.

---

### Post by fewjr on 2008-12-25
Oh I'm sorry overdrank, I didn't see that second part there. I need to check on which nVidia driver I'm using. I think the 177. The thing is the cube and all the effects work well. I was just wondering if it is a Firefox issue. I had the same problem with Hardy towards the end with 8.04.1, but not when it was just 8.04, when I first started using Ubuntu. Its Christmas night and I'm at work. I'll post when I double check.

Thanks
fewjr

---

### Post by fewjr on 2008-12-25
Okay overdrank.....envyNG shows that I am using nVidia driver version 173.14.12-1-0ubuntu4. It is the recommended driver it says. 177.80-0ubuntu4 is shown above it. I can't remember if I tried it out to see if it would help or not. Its been awhile and I haven't had time to fix this. I just stopped using compiz-fusion. I really like the cube and find it useful, so what do you think I should do? Hope you had a nice Christmas.

fewjr

---

### Post by fewjr on 2008-12-27
Hello Again,
 Something else I've noticed in the last couple days, while I have extra effects enabled (Compiz-fusion). When I'm scrolling through a webpage and it starts to jumble up together and get corrupt, if I hit the 'print screen' key it fixes the page, but as soon as I start to scroll the page again it starts to corrupt the page again. I wanted to post an image of the page so you could see it and thats when I noticed this.

fewjr

---

