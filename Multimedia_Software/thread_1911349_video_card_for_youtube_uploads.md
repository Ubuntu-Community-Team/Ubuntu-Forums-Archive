---
title: "video card for youtube uploads"
date: 2012-01-18
forum: Multimedia Software
---

### Post by badmts on 2012-01-18
I have a few extra dollars thanks to some holiday overtime and want to treat myself to a video card .I couldn't tell you much about my current configuration other than to tell you it is a used/refurb PC bought from a local shop for $150.00 so it can't be too great but it seems to do me fine so far.I would like to start using OPENSHOT to post some vids to youtube -Right now I pretty much surf the web is all I do so if you have other ideas please let me know.

---

### Post by wolfen69 on 2012-01-18
Give us the output of
```
lspci
```

---

### Post by badmts on 2012-01-19
robert@robert-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by MoreOrLess on 2012-01-19
You probably don't even have an AGP slot. $150 seems like overkill. Anyway.. 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500228](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500228)

---

### Post by mips on 2012-01-19
Open the PC up and post a picture of the motherboard here. We need to find out if it has a AGP, PCI or PCIe slot before we can tell you anything.

---

### Post by MoreOrLess on 2012-01-19
> **mips said:**
> Open the PC up and post a picture of the motherboard here. We need to find out if it has a AGP, PCI or PCIe slot before we can tell you anything.

I think the AGP controller would show up under lspci, no? dmidecode will hopefully show the mobo model and that can be googled, which is a lot faster than opening up the system and posting a screenshot.

---

### Post by badmts on 2012-01-19
opening machine is NOT out of the question as I have a firewire adapter card coming from amazon in a few says anyway . if i open it to find no place on MOBO  is maxing out RAM ok for just youtubing or should I get a used MOBO and a video card .I am mainly trying to avoid slow uploads to YOUTUBE via OPENSHOT that I have read about

---

### Post by mips on 2012-01-19
Post the output of **lspci -v** &  **sudo dmidecode** as MoreOrLess suggested and copy the output to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and post the link here.

---

### Post by badmts on 2012-01-19
robert@robert-desktop:~$ lspci-v
lspci-v: command not found
robert@robert-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ed98 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Flags: fast devsel
    Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: medium devsel, IRQ 3
    I/O ports at eda0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
    Subsystem: Linksys Device 0055
    Flags: bus master, slow devsel, latency 64, IRQ 21
    Memory at feaf8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
    Subsystem: Dell Device 1000
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 22
    Memory at feaf6000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at de00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at feaf7000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ddc0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

---

### Post by badmts on 2012-01-19
```
Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

Handle 0x0100, DMI type 1, 25 bytes
System Information
    Manufacturer: Dell Computer Corporation
    Product Name: Dimension 3000               
    Version: Not Specified
    Serial Number: 3F8DL61
    UUID: 44454C4C-4600-1038-8044-B3C04F4C3631
    Wake-up Type: Power Switch

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Dell Computer Corp.
    Product Name: 0N6381
    Version:    
    Serial Number: ..CN481114BT003Y.

Handle 0x0300, DMI type 3, 13 bytes
Chassis Information
    Manufacturer: Dell Computer Corporation
    Type: Mini Tower
    Lock: Not Present
    Version: Not Specified
    Serial Number: 3F8DL61
    Asset Tag:           
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None

Handle 0x0400, DMI type 4, 32 bytes
Processor Information
    Socket Designation: Microprocessor
    Type: Central Processor
    Family: Pentium 4
    Manufacturer: Intel
    ID: 33 0F 00 00 FF FB EB BF
    Signature: Type 0, Family 15, Model 3, Stepping 3
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
    Version: Not Specified
    Voltage: 1.1 V
    External Clock: 800 MHz
    Max Speed: 3600 MHz
    Current Speed: 2800 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0700
    L2 Cache Handle: 0x0701
    L3 Cache Handle: Not Provided

Handle 0x0700, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Not Specified
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 16 KB
    Maximum Size: 16 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Data
    Associativity: Other

Handle 0x0701, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Not Specified
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: Other

Handle 0x0704, DMI type 126, 19 bytes
Inactive

Handle 0x0800, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PARALLEL
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: DB-25 female
    Port Type: Parallel Port PS/2

Handle 0x0801, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SERIAL1
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x0803, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: KYBD
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0804, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: MOUSE
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0805, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB1
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0806, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB2
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0807, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB3
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0808, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB4
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0809, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB5
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x080A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB6
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x080D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ENET
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x080E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: MIC
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x080F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LINE-OUT
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0810, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LINE-IN
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0811, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: HP-OUT
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0812, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: MONITOR
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0901, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PME signal is supported

Handle 0x0902, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: In Use
    Length: Long
    ID: 2
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PME signal is supported

Handle 0x0903, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 3
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PME signal is supported

Handle 0x0904, DMI type 126, 13 bytes
Inactive

Handle 0x0905, DMI type 126, 13 bytes
Inactive

Handle 0x0A00, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description: Intel 865-G PCI Accelerated SVGA

Handle 0x0A02, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Intel Pro 100 VE Network Connection

Handle 0x0A03, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: AC'97 Audio Controller

Handle 0x0B00, DMI type 11, 5 bytes
OEM Strings
    String 1: [www.dell.com](www.dell.com)

Handle 0x0D00, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0F00, DMI type 15, 29 bytes
System Event Log
    Area Length: 2049 bytes
    Header Start Offset: 0x0000
    Header Length: 16 bytes
    Data Start Offset: 0x0010
    Access Method: Memory-mapped physical 32-bit address
    Access Address: 0xFFF82000
    Status: Valid, Not Full
    Change Token: 0x0000000F
    Header Format: Type 1
    Supported Log Type Descriptors: 3
    Descriptor 1: POST error
    Data Format 1: POST results bitmap
    Descriptor 2: System limit exceeded
    Data Format 2: System management
    Descriptor 3: Log area reset/cleared
    Data Format 3: None

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x1100, DMI type 17, 23 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_1
    Bank Locator: Not Specified
    Type: SDRAM
    Type Detail: Synchronous
    Speed: 400 MHz (2.5 ns)

Handle 0x1101, DMI type 17, 23 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_2
    Bank Locator: Not Specified
    Type: SDRAM
    Type Detail: Synchronous
    Speed: 400 MHz (2.5 ns)

Handle 0x1301, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Array Handle: 0x1000
    Partition Width: 0

Handle 0x1402, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x1100
    Memory Array Mapped Address Handle: 0x1301
    Partition Row Position: 1

Handle 0x1403, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x1101
    Memory Array Mapped Address Handle: 0x1301
    Partition Row Position: 1

Handle 0x1800, DMI type 24, 5 bytes
Hardware Security
    Power-On Password Status: Enabled
    Keyboard Password Status: Not Implemented
    Administrator Password Status: Enabled
    Front Panel Reset Status: Not Implemented

Handle 0x1900, DMI type 25, 9 bytes
    System Power Controls
    Next Scheduled Power-on: *-* 00:00:00

Handle 0x1B00, DMI type 27, 12 bytes
Cooling Device
    Type: Fan
    Status: OK
    OEM-specific Information: 0x00000000

Handle 0x1F00, DMI type 31, 28 bytes
Boot Integrity Services Entry Point

Handle 0x2000, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0xD000, DMI type 208, 10 bytes
OEM-specific Type
    Header and Data:
        D0 0A 00 D0 01 03 FE 00 9D 01

Handle 0xD100, DMI type 209, 12 bytes
OEM-specific Type
    Header and Data:
        D1 0C 00 D1 78 03 07 03 04 0F 80 05

Handle 0xD200, DMI type 210, 12 bytes
OEM-specific Type
    Header and Data:
        D2 0C 00 D2 F8 03 04 03 06 80 04 05

Handle 0xD400, DMI type 212, 177 bytes
OEM-specific Type
    Header and Data:
        D4 B1 00 D4 70 00 71 00 00 10 2D 2E 42 00 11 FE
        01 43 00 11 FE 00 0F 00 25 FC 00 10 00 25 FC 01
        11 00 25 FC 02 12 00 25 FC 03 07 00 23 8F 00 08
        00 23 F3 00 09 00 23 F3 04 0A 00 23 F3 08 0B 00
        23 8F 10 0C 00 23 8F 20 0E 00 23 8F 30 0D 00 23
        8C 40 A6 00 23 8C 41 A7 00 23 8C 42 05 01 22 FD
        02 06 01 22 FD 00 8C 00 22 FE 00 8D 00 22 FE 01
        9B 00 25 3F 40 9C 00 25 3F 00 09 01 25 3F 80 A8
        00 26 FE 01 A9 00 26 FE 00 A1 00 26 F3 00 A2 00
        26 F3 08 A3 00 26 F3 04 9F 00 26 FD 02 A0 00 26
        FD 00 9D 00 11 FB 04 9E 00 11 FB 00 FF FF 00 00
        00

Handle 0xD401, DMI type 212, 207 bytes
OEM-specific Type
    Header and Data:
        D4 CF 01 D4 70 00 71 00 03 40 59 6D 2D 00 59 FC
        02 2E 00 59 FC 00 6E 00 59 FC 01 28 00 59 3F 00
        29 00 59 3F 40 2A 00 59 3F 80 2B 00 5A 00 00 2C
        00 5B 00 00 55 00 59 F3 00 6D 00 59 F3 04 5C 00
        78 BF 40 5D 00 78 BF 00 04 80 78 F5 0A 01 A0 78
        F5 00 1C 00 55 FB 04 1D 00 55 FB 00 19 00 55 E7
        00 1A 00 55 E7 08 1B 00 55 E7 10 93 00 7B 7F 80
        94 00 7B 7F 00 23 00 55 7F 00 22 00 55 7F 80 03
        C0 67 00 05 8A 00 37 DF 20 8B 00 37 DF 00 AC 00
        51 CF 30 AD 00 51 CF 00 AE 00 51 CF 10 AF 00 51
        CF 20 F5 00 58 BF 40 F6 00 58 BF 00 EB 00 55 FE
        00 EA 00 55 FE 01 01 01 51 3F 00 02 01 51 3F 40
        03 01 51 3F 80 04 01 51 3F C0 FF FF 00 00 00

Handle 0xD402, DMI type 212, 77 bytes
OEM-specific Type
    Header and Data:
        D4 4D 02 D4 70 00 71 00 00 10 2D 2E 2D 01 21 FE
        01 2E 01 21 FE 00 2F 01 21 7F 00 30 01 21 7F 80
        E2 00 27 7F 00 E3 00 27 7F 80 E4 00 27 BF 00 E5
        00 27 BF 40 07 01 27 DF 20 08 01 27 DF 00 D1 00
        22 7F 80 D2 00 22 7F 00 FF FF 00 00 00

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
    Header and Data:
        D8 09 00 D8 01 02 01 F0 03
    Strings:
        Intel(r)865G PCI Accelerated SVGA
        2972 PC Dev    04/16/2003  13:01:21

Handle 0xDE00, DMI type 222, 13 bytes
OEM-specific Type
    Header and Data:
        DE 0D 00 DE C1 01 FF FF 00 00 00 00 00

Handle 0xDF00, DMI type 223, 33 bytes
OEM-specific Type
    Header and Data:
        DF 21 00 DF 0C 00 11 FF FF FF FF FF FF FF FF FF
        FF FF FF 01 11 7F 98 00 00 00 00 00 00 6A 3F 4F
        01

Handle 0xDF01, DMI type 126, 33 bytes
Inactive

Handle 0x7F00, DMI type 127, 4 bytes
End Of Table
```

---

### Post by MoreOrLess on 2012-01-19
No AGP slots.. ;( Why do you need a new video card for uploading anyway?

---

### Post by mips on 2012-01-19
That PC has no AGP slot so your only option is a old PCI (NOT PCIe) video card. Maybe you can find one second hand?

New ones,
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853&IsNodeId=1&name=PCI](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853&IsNodeId=1&name=PCI)

I actually think you paid to much money for that PC.

---

### Post by badmts on 2012-01-19
I just thought it would help:confused:  I am super new to computing/Linux/YouTUBE You guys have been MORE than helpful. Heck I learned some things just by performing the tasks given me by mips and moreorless . Please DO NOT think your time was WASTED -IT WAS NOT! THIS UBUNTU THING IS GREAT- as are YOU!! :KS      Now I am going to call the computer store and see about a MOBO/RAM/VIDEO CARD UPGRADE :P

---

### Post by mips on 2012-01-20
> **badmts said:**
>      Now I am going to call the computer store and see about a MOBO/RAM/VIDEO CARD UPGRADE :P

Hang on there before calling anyone.

Tell us your budget, main purpose of using the computer etc.

We could help you put together something that fits your budget and meets your needs.

Are you in the USA? Reason I ask is so we can point you to online or local shops/special deals ;)

---

