---
title: "Intel(R) Centrino® Advanced-N 6205 For Desktop - Failed to run INIT ucode: -110"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by jack2000 on 2012-09-24
**1 ) Machine Brand and Model (PC/Laptop):**
Homebuilt Rig (Nontechnical Friend's Computer)
EVGA 132-CK-NF78-A1 with Intel(R) Core(TM)2 Quad CPU Q6600  @ 2.40GHz stepping 0b

dmidecode
```

# dmidecode 2.11
SMBIOS 2.4 present.
38 structures occupying 1124 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 01/16/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
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
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
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
    Manufacturer:  EVGA 
    Product Name: 132-CK-NF78
    Version: 2
    Serial Number: 1
    UUID: CC3ED15A-164B-0400-0000-000000000000
    Wake-up Type: Power Switch
    SKU Number:  
    Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer:  EVGA 
    Product Name: 132-CK-NF78
    Version: 2
    Serial Number: 1

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer:  EVGA 
    Type: Desktop
    Lock: Not Present
    Version: 132-CK-NF78
    Serial Number:  
    Asset Tag:  
    Boot-up State: Unknown
    Power Supply State: Unknown
    Thermal State: Unknown
    Security Status: Unknown
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket 775
    Type: Central Processor
    Family: Other
    Manufacturer: Intel
    ID: FB 06 00 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 15, Stepping 11
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
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM)2 Quad CPU
    Voltage: 1.7 V
    External Clock: 267 MHz
    Max Speed: 200 MHz
    Current Speed: 2403 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x000A
    L2 Cache Handle: 0x000B
    L3 Cache Handle: Not Provided
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 32 MB
    Maximum Total Memory Size: 128 MB
    Supported Speeds:
        70 ns
        60 ns
    Supported Memory Types:
        Standard
        EDO
    Memory Module Voltage: 5.0 V
    Associated Memory Slots: 4
        0x0006
        0x0007
        0x0008
        0x0009
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2 3
    Current Speed: 10 ns
    Type: Other
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: None
    Current Speed: 10 ns
    Type: Other
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: None
    Current Speed: 10 ns
    Type: Other
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x000A, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Internal Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: None
    System Type: Instruction
    Associativity: 8-way Set-associative

Handle 0x000B, DMI type 7, 19 bytes
Cache Information
    Socket Designation: External Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: External
    Installed Size: 4096 kB
    Maximum Size: 4096 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB0
    External Connector Type: Other
    Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Other
    Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Other
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Other
    Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Other
    Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Other
    Port Type: USB

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI0
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0018, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0019, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: 128 bits
    Data Width: 128 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: DRAM
    Type Detail: None
    Speed: 800 MHz
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: DRAM
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: DRAM
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001F, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Physical Array Handle: 0x001A
    Partition Width: 1

Handle 0x0020, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x001B
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0021, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x001C
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0022, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x001D
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0023, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x001E
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0024, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0025, DMI type 127, 4 bytes
End Of Table

```**2 ) Wireless Brand, Model and Wireless Chipset:**
Intel(R) Centrino® Advanced-N 6205 For Desktop
Product Code: 62205ANHMWDTX1
UPC: 735858246309
EAN: 5032037040792
MM#: 921440
Batch#: CNWZ28E3BU

lspci -vvv (only device in question)
```

07:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 4 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at cfdfe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0f00c  Data: 4181
    Capabilities: [e0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <32us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [140 v1] Device Serial Number 8c-70-5a-ff-ff-7d-8e-08
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```lspci -nn
```

07:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)

```**3 ) check interface:**
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:04:4b:14:ec:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:14:ec:0d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe14:ec0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4315233 (4.3 MB)  TX bytes:625695 (625.6 KB)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16360 (16.3 KB)  TX bytes:16360 (16.3 KB)

```iwconfig
```

lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

```**4 ) Check for modules:**

lsmod (iwlwifi)
```

Module                  Size  Used by
iwlwifi               396989  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211

```**5 ) Kernel boot messages**

dmesg (all over the place, didn't redact as there is a lot good information)
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic 3.2.28)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=19757f4d-ef71-4b69-bf0e-0a920dc05535 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000150000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:  EVGA  132-CK-NF78/132-CK-NF78, BIOS 6.00 PG 01/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x150000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 100000000 mask FC0000000 write-back
[    0.000000]   1 base 140000000 mask FF0000000 write-back
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 base 080000000 mask FE0000000 write-back
[    0.000000]   4 base 0A0000000 mask FF0000000 write-back
[    0.000000]   5 base 0AFF00000 mask FFFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 4GB, range: 1GB, type WB
[    0.000000] reg 1, base: 5GB, range: 256MB, type WB
[    0.000000] reg 2, base: 0GB, range: 2GB, type WB
[    0.000000] reg 3, base: 2GB, range: 512MB, type WB
[    0.000000] reg 4, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 5, base: 2815MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] reg 5, base: 5GB, range: 256MB, type WB
[    0.000000] e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xafef0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f4020] f4020
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000afef0000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00afef0000 page 4k
[    0.000000] kernel direct mapping tables up to afef0000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000150000000
[    0.000000]  0100000000 - 0150000000 page 2M
[    0.000000] kernel direct mapping tables up to 150000000 @ afee9000-afef0000
[    0.000000] RAMDISK: 364dc000 - 37266000
[    0.000000] ACPI: RSDP 00000000000f7fe0 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 00000000afef3040 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 00000000afef30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 00000000afef3180 05283 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000afef0000 00040
[    0.000000] ACPI: HPET 00000000afef8580 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 00000000afef8600 00047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 00000000afef86c0 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 00000000afef8480 00098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000150000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000150000000
[    0.000000]   NODE_DATA [000000014fffb000 - 000000014fffffff]
[    0.000000]  [ffffea0000000000-ffffea00053fffff] PMD -> [ffff88014b600000-ffff88014f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00150000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000afef0
[    0.000000]     0: 0x00100000 -> 0x00150000
[    0.000000] On node 0 totalpages: 1048187
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3910 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 700208 pages, LIFO batch:31
[    0.000000]   Normal zone: 5120 pages used for memmap
[    0.000000]   Normal zone: 322560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afef0000 - 00000000afef3000
[    0.000000] PM: Registered nosave memory: 00000000afef3000 - 00000000aff00000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:20100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88014fc00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1026678
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic root=UUID=19757f4d-ef71-4b69-bf0e-0a920dc05535 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4031012k/5505024k available (6558k kernel code, 1312276k absent, 161736k reserved, 6642k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2400.162 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.32 BogoMIPS (lpj=9600648)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004034] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004054] Yama: becoming mindful.
[    0.004419] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009298] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010307] Mount-cache hash table entries: 256
[    0.010470] Initializing cgroup subsys cpuacct
[    0.010477] Initializing cgroup subsys memory
[    0.010486] Initializing cgroup subsys devices
[    0.010488] Initializing cgroup subsys freezer
[    0.010491] Initializing cgroup subsys blkio
[    0.010498] Initializing cgroup subsys perf_event
[    0.010529] CPU: Physical Processor ID: 0
[    0.010530] CPU: Processor Core ID: 0
[    0.010533] mce: CPU supports 6 MCE banks
[    0.010541] CPU0: Thermal monitoring enabled (TM1)
[    0.010546] using mwait in idle threads.
[    0.012965] ACPI: Core revision 20110623
[    0.016013] ftrace: allocating 27008 entries in 106 pages
[    0.020530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063819] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 96000
[    0.152031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152132]  #2
[    0.152134] smpboot cpu 2: start_ip = 96000
[    0.244044] NMI watchdog enabled, takes one hw-pmu counter.
[    0.244145]  #3 Ok.
[    0.244147] smpboot cpu 3: start_ip = 96000
[    0.336040] NMI watchdog enabled, takes one hw-pmu counter.
[    0.336068] Brought up 4 CPUs
[    0.336071] Total of 4 processors activated (19200.23 BogoMIPS).
[    0.339489] devtmpfs: initialized
[    0.340851] EVM: security.selinux
[    0.340852] EVM: security.SMACK64
[    0.340854] EVM: security.capability
[    0.340890] PM: Registering ACPI NVS region at afef0000 (12288 bytes)
[    0.340890] print_constraints: dummy: 
[    0.340890] RTC time:  2:19:42, date: 09/23/12
[    0.340890] NET: Registered protocol family 16
[    0.340890] Trying to unpack rootfs image as initramfs...
[    0.340982] ACPI: bus type pci registered
[    0.341044] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.341047] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.385003] PCI: Using configuration type 1 for base access
[    0.386648] bio: create slab <bio-0> at 0
[    0.387005] ACPI: Added _OSI(Module Device)
[    0.387005] ACPI: Added _OSI(Processor Device)
[    0.387005] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.387005] ACPI: Added _OSI(Processor Aggregator Device)
[    0.388407] ACPI: EC: Look up EC in DSDT
[    0.392323] ACPI: Interpreter enabled
[    0.392329] ACPI: (supports S0 S3 S4 S5)
[    0.392348] ACPI: Using IOAPIC for interrupt routing
[    0.397406] ACPI: No dock devices found.
[    0.397409] HEST: Table not found.
[    0.397412] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.397483] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.397581] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.397584] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.397586] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.397588] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.397591] pci_root PNP0A08:00: host bridge window [mem 0xaff00000-0xcfffffff]
[    0.397607] pci 0000:00:00.0: [10de:03a1] type 0 class 0x000600
[    0.397669] pci 0000:00:00.1: [10de:03ac] type 0 class 0x000500
[    0.397742] pci 0000:00:00.2: [10de:03aa] type 0 class 0x000500
[    0.397809] pci 0000:00:00.3: [10de:03a9] type 0 class 0x000500
[    0.397877] pci 0000:00:00.4: [10de:03ab] type 0 class 0x000500
[    0.397945] pci 0000:00:00.5: [10de:03a8] type 0 class 0x000500
[    0.398002] pci 0000:00:00.6: [10de:03b5] type 0 class 0x000500
[    0.398073] pci 0000:00:00.7: [10de:03b4] type 0 class 0x000500
[    0.398140] pci 0000:00:01.0: [10de:03ad] type 0 class 0x000500
[    0.398196] pci 0000:00:01.1: [10de:03ae] type 0 class 0x000500
[    0.398254] pci 0000:00:01.2: [10de:03af] type 0 class 0x000500
[    0.398311] pci 0000:00:01.3: [10de:03b0] type 0 class 0x000500
[    0.398367] pci 0000:00:01.4: [10de:03b1] type 0 class 0x000500
[    0.398422] pci 0000:00:01.5: [10de:03b2] type 0 class 0x000500
[    0.398481] pci 0000:00:01.6: [10de:03b3] type 0 class 0x000500
[    0.398549] pci 0000:00:02.0: [10de:03b6] type 0 class 0x000500
[    0.398606] pci 0000:00:02.1: [10de:03bc] type 0 class 0x000500
[    0.398675] pci 0000:00:02.2: [10de:03ba] type 0 class 0x000500
[    0.398791] pci 0000:00:03.0: [10de:03b7] type 1 class 0x000604
[    0.398837] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.398841] pci 0000:00:03.0: PME# disabled
[    0.398877] pci 0000:00:09.0: [10de:0369] type 0 class 0x000500
[    0.399080] pci 0000:00:0a.0: [10de:0360] type 0 class 0x000601
[    0.399090] pci 0000:00:0a.0: reg 10: [io  0xfc00-0xfc7f]
[    0.399139] pci 0000:00:0a.1: [10de:0368] type 0 class 0x000c05
[    0.399155] pci 0000:00:0a.1: reg 10: [io  0xf800-0xf83f]
[    0.399182] pci 0000:00:0a.1: reg 20: [io  0xf400-0xf43f]
[    0.399190] pci 0000:00:0a.1: reg 24: [io  0xf000-0xf03f]
[    0.399229] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.399235] pci 0000:00:0a.1: PME# disabled
[    0.399258] pci 0000:00:0b.0: [10de:036c] type 0 class 0x000c03
[    0.399270] pci 0000:00:0b.0: reg 10: [mem 0xcffff000-0xcfffffff]
[    0.399321] pci 0000:00:0b.0: supports D1 D2
[    0.399323] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399327] pci 0000:00:0b.0: PME# disabled
[    0.399342] pci 0000:00:0b.1: [10de:036d] type 0 class 0x000c03
[    0.399357] pci 0000:00:0b.1: reg 10: [mem 0xcfffe000-0xcfffe0ff]
[    0.399412] pci 0000:00:0b.1: supports D1 D2
[    0.399414] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399417] pci 0000:00:0b.1: PME# disabled
[    0.399439] pci 0000:00:0d.0: [10de:036e] type 0 class 0x000101
[    0.399468] pci 0000:00:0d.0: reg 20: [io  0xec00-0xec0f]
[    0.399508] pci 0000:00:0e.0: [10de:037f] type 0 class 0x000101
[    0.399522] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
[    0.399529] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.399537] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
[    0.399544] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
[    0.399551] pci 0000:00:0e.0: reg 20: [io  0xd800-0xd80f]
[    0.399558] pci 0000:00:0e.0: reg 24: [mem 0xcfffd000-0xcfffdfff]
[    0.399607] pci 0000:00:0e.1: [10de:037f] type 0 class 0x000101
[    0.399620] pci 0000:00:0e.1: reg 10: [io  0x09e0-0x09e7]
[    0.399627] pci 0000:00:0e.1: reg 14: [io  0x0be0-0x0be3]
[    0.399634] pci 0000:00:0e.1: reg 18: [io  0x0960-0x0967]
[    0.399641] pci 0000:00:0e.1: reg 1c: [io  0x0b60-0x0b63]
[    0.399648] pci 0000:00:0e.1: reg 20: [io  0xc400-0xc40f]
[    0.399655] pci 0000:00:0e.1: reg 24: [mem 0xcfffc000-0xcfffcfff]
[    0.399703] pci 0000:00:0e.2: [10de:037f] type 0 class 0x000101
[    0.399718] pci 0000:00:0e.2: reg 10: [io  0xc000-0xc007]
[    0.399725] pci 0000:00:0e.2: reg 14: [io  0xbc00-0xbc03]
[    0.399732] pci 0000:00:0e.2: reg 18: [io  0xb800-0xb807]
[    0.399739] pci 0000:00:0e.2: reg 1c: [io  0xb400-0xb403]
[    0.399746] pci 0000:00:0e.2: reg 20: [io  0xb000-0xb00f]
[    0.399753] pci 0000:00:0e.2: reg 24: [mem 0xcfffb000-0xcfffbfff]
[    0.399805] pci 0000:00:0f.0: [10de:0370] type 1 class 0x000604
[    0.399860] pci 0000:00:0f.1: [10de:0371] type 0 class 0x000403
[    0.399875] pci 0000:00:0f.1: reg 10: [mem 0xcfff0000-0xcfff3fff]
[    0.399940] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.399943] pci 0000:00:0f.1: PME# disabled
[    0.399973] pci 0000:00:11.0: [10de:0373] type 0 class 0x000680
[    0.399989] pci 0000:00:11.0: reg 10: [mem 0xcfffa000-0xcfffafff]
[    0.399996] pci 0000:00:11.0: reg 14: [io  0xac00-0xac07]
[    0.400004] pci 0000:00:11.0: reg 18: [mem 0xcfff9000-0xcfff90ff]
[    0.400011] pci 0000:00:11.0: reg 1c: [mem 0xcfff8000-0xcfff800f]
[    0.400083] pci 0000:00:11.0: supports D1 D2
[    0.400085] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.400090] pci 0000:00:11.0: PME# disabled
[    0.400116] pci 0000:00:12.0: [10de:0373] type 0 class 0x000680
[    0.400133] pci 0000:00:12.0: reg 10: [mem 0xcfff7000-0xcfff7fff]
[    0.400140] pci 0000:00:12.0: reg 14: [io  0xa800-0xa807]
[    0.400147] pci 0000:00:12.0: reg 18: [mem 0xcfff6000-0xcfff60ff]
[    0.400154] pci 0000:00:12.0: reg 1c: [mem 0xcfff5000-0xcfff500f]
[    0.400205] pci 0000:00:12.0: supports D1 D2
[    0.400207] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.400212] pci 0000:00:12.0: PME# disabled
[    0.400234] pci 0000:00:13.0: [10de:0376] type 1 class 0x000604
[    0.400286] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.400289] pci 0000:00:13.0: PME# disabled
[    0.400315] pci 0000:00:16.0: [10de:0378] type 1 class 0x000604
[    0.400365] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.400369] pci 0000:00:16.0: PME# disabled
[    0.400428] pci 0000:01:00.0: [10de:05b1] type 1 class 0x000604
[    0.400482] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.400486] pci 0000:01:00.0: PME# disabled
[    0.408043] pci 0000:00:03.0: PCI bridge to [bus 01-04]
[    0.408049] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.408052] pci 0000:00:03.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.408056] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.408097] pci 0000:02:00.0: [10de:05b1] type 1 class 0x000604
[    0.408148] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.408152] pci 0000:02:00.0: PME# disabled
[    0.408172] pci 0000:02:02.0: [10de:05b1] type 1 class 0x000604
[    0.408220] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.408223] pci 0000:02:02.0: PME# disabled
[    0.408254] pci 0000:01:00.0: PCI bridge to [bus 02-04]
[    0.408259] pci 0000:01:00.0:   bridge window [io  0x9000-0x9fff]
[    0.408263] pci 0000:01:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.408268] pci 0000:01:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.408307] pci 0000:03:00.0: [10de:0611] type 0 class 0x000300
[    0.408320] pci 0000:03:00.0: reg 10: [mem 0xcc000000-0xccffffff]
[    0.408334] pci 0000:03:00.0: reg 14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.408348] pci 0000:03:00.0: reg 1c: [mem 0xca000000-0xcbffffff 64bit]
[    0.408358] pci 0000:03:00.0: reg 24: [io  0x9c00-0x9c7f]
[    0.408368] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.416045] pci 0000:02:00.0: PCI bridge to [bus 03-03]
[    0.416051] pci 0000:02:00.0:   bridge window [io  0x9000-0x9fff]
[    0.416055] pci 0000:02:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.416060] pci 0000:02:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.416088] pci 0000:02:02.0: PCI bridge to [bus 04-04]
[    0.416151] pci 0000:05:07.0: [104c:8023] type 0 class 0x000c00
[    0.416167] pci 0000:05:07.0: reg 10: [mem 0xcfeff000-0xcfeff7ff]
[    0.416176] pci 0000:05:07.0: reg 14: [mem 0xcfef8000-0xcfefbfff]
[    0.416235] pci 0000:05:07.0: supports D1 D2
[    0.416237] pci 0000:05:07.0: PME# supported from D0 D1 D2 D3hot
[    0.416241] pci 0000:05:07.0: PME# disabled
[    0.416276] pci 0000:00:0f.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.416281] pci 0000:00:0f.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.416285] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.416288] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.416290] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.416292] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.416295] pci 0000:00:0f.0:   bridge window [mem 0xaff00000-0xcfffffff] (subtractive decode)
[    0.416332] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.416402] pci 0000:07:00.0: [8086:0082] type 0 class 0x000280
[    0.416432] pci 0000:07:00.0: reg 10: [mem 0xcfdfe000-0xcfdfffff 64bit]
[    0.416573] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.416579] pci 0000:07:00.0: PME# disabled
[    0.424049] pci 0000:00:16.0: PCI bridge to [bus 07-07]
[    0.424056] pci 0000:00:16.0:   bridge window [mem 0xcfd00000-0xcfdfffff]
[    0.424079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.424299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.424468]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.424519]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.456053] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456101] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456147] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456192] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.456236] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.456279] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456323] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 *10 11 14 15)
[    0.456365] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456410] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.456453] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.456496] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.456547] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.456590] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456634] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.456680] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.456725] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 *10 11 14 15)
[    0.456773] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.456817] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[    0.456900] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.456966] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.457030] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.457095] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.457159] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.457230] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.457294] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0
[    0.457358] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.457422] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.457487] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
[    0.457556] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0
[    0.457622] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.457686] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[    0.457752] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[    0.457817] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[    0.457882] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[    0.457946] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[    0.458012] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[    0.458076] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[    0.458140] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.458258] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.458258] vgaarb: loaded
[    0.458258] vgaarb: bridge control possible 0000:03:00.0
[    0.458258] i2c-core: driver [aat2870] using legacy suspend method
[    0.458258] i2c-core: driver [aat2870] using legacy resume method
[    0.458258] SCSI subsystem initialized
[    0.458558] libata version 3.00 loaded.
[    0.458558] usbcore: registered new interface driver usbfs
[    0.458558] usbcore: registered new interface driver hub
[    0.458907] usbcore: registered new device driver usb
[    0.459183] PCI: Using ACPI for IRQ routing
[    0.466620] PCI: pci_cache_line_size set to 64 bytes
[    0.466756] reserve RAM buffer: 000000000009b800 - 000000000009ffff 
[    0.466759] reserve RAM buffer: 00000000afef0000 - 00000000afffffff 
[    0.466885] NetLabel: Initializing
[    0.466888] NetLabel:  domain hash size = 128
[    0.466889] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.466900] NetLabel:  unlabeled traffic allowed by default
[    0.466936] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.466936] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.466936] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.476952] Switching to clocksource hpet
[    0.483785] AppArmor: AppArmor Filesystem Enabled
[    0.483821] pnp: PnP ACPI init
[    0.483842] ACPI: bus type pnp registered
[    0.483877] pnp 00:00: [io  0x1000-0x107f]
[    0.483879] pnp 00:00: [io  0x1080-0x10ff]
[    0.483881] pnp 00:00: [io  0x1400-0x147f]
[    0.483883] pnp 00:00: [io  0x1480-0x14ff]
[    0.483884] pnp 00:00: [io  0x1800-0x187f]
[    0.483886] pnp 00:00: [io  0x1880-0x18ff]
[    0.483970] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.483972] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.483975] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.483977] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.483979] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.483982] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.483985] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.484102] pnp 00:01: [bus 00-ff]
[    0.484104] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.484106] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.484108] pnp 00:01: [io  0x0d00-0xffff window]
[    0.484110] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.484112] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.484114] pnp 00:01: [mem 0xaff00000-0xcfffffff window]
[    0.484180] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.484242] pnp 00:02: [io  0x0010-0x001f]
[    0.484244] pnp 00:02: [io  0x0022-0x003f]
[    0.484246] pnp 00:02: [io  0x0044-0x005f]
[    0.484248] pnp 00:02: [io  0x0062-0x0063]
[    0.484249] pnp 00:02: [io  0x0065-0x006f]
[    0.484251] pnp 00:02: [io  0x0074-0x007f]
[    0.484253] pnp 00:02: [io  0x0091-0x0093]
[    0.484254] pnp 00:02: [io  0x00a2-0x00bf]
[    0.484256] pnp 00:02: [io  0x00e0-0x00ef]
[    0.484258] pnp 00:02: [io  0x04d0-0x04d1]
[    0.484259] pnp 00:02: [io  0x0295-0x0314]
[    0.484261] pnp 00:02: [io  0x0880-0x088f]
[    0.484328] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.484331] system 00:02: [io  0x0295-0x0314] has been reserved
[    0.484334] system 00:02: [io  0x0880-0x088f] has been reserved
[    0.484337] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.484348] pnp 00:03: [dma 4]
[    0.484349] pnp 00:03: [io  0x0000-0x000f]
[    0.484351] pnp 00:03: [io  0x0080-0x0090]
[    0.484353] pnp 00:03: [io  0x0094-0x009f]
[    0.484359] pnp 00:03: [io  0x00c0-0x00df]
[    0.484394] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.484432] pnp 00:04: [irq 0 disabled]
[    0.484444] pnp 00:04: [irq 8]
[    0.484446] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
[    0.484481] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.484501] pnp 00:05: [io  0x0070-0x0071]
[    0.484503] pnp 00:05: [io  0x0072-0x0073]
[    0.484538] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.484546] pnp 00:06: [io  0x0061]
[    0.484581] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.484589] pnp 00:07: [io  0x00f0-0x00ff]
[    0.484594] pnp 00:07: [irq 13]
[    0.484626] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.484724] pnp 00:08: [io  0x03f0-0x03f5]
[    0.484726] pnp 00:08: [io  0x03f7]
[    0.484731] pnp 00:08: [irq 6]
[    0.484733] pnp 00:08: [dma 2]
[    0.484785] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.484922] pnp 00:09: [io  0x03f8-0x03ff]
[    0.484928] pnp 00:09: [irq 4]
[    0.484991] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.485023] pnp 00:0a: [io  0x0060]
[    0.485025] pnp 00:0a: [io  0x0064]
[    0.485029] pnp 00:0a: [irq 1]
[    0.485070] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.485565] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.485641] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.485644] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.485744] pnp 00:0c: [mem 0x000d0000-0x000d3fff]
[    0.485746] pnp 00:0c: [mem 0x000d5800-0x000d7fff]
[    0.485748] pnp 00:0c: [mem 0x000f0000-0x000fbfff]
[    0.485750] pnp 00:0c: [mem 0x000fc000-0x000fffff]
[    0.485752] pnp 00:0c: [mem 0xafef0000-0xafefffff]
[    0.485754] pnp 00:0c: [mem 0xffff0000-0xffffffff]
[    0.485756] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.485757] pnp 00:0c: [mem 0x00100000-0xafeeffff]
[    0.485759] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.485761] pnp 00:0c: [mem 0xd0000000-0xdfffffff]
[    0.485763] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.485765] pnp 00:0c: [mem 0xfeff0000]
[    0.485844] system 00:0c: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.485847] system 00:0c: [mem 0x000d5800-0x000d7fff] has been reserved
[    0.485849] system 00:0c: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.485852] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.485855] system 00:0c: [mem 0xafef0000-0xafefffff] could not be reserved
[    0.485857] system 00:0c: [mem 0xffff0000-0xffffffff] has been reserved
[    0.485860] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.485862] system 00:0c: [mem 0x00100000-0xafeeffff] could not be reserved
[    0.485865] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.485867] system 00:0c: [mem 0xd0000000-0xdfffffff] has been reserved
[    0.485870] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.485872] system 00:0c: [mem 0xfeff0000] has been reserved
[    0.485875] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.485883] pnp: PnP ACPI: found 13 devices
[    0.485884] ACPI: ACPI bus type pnp unregistered
[    0.493839] PCI: max bus depth: 3 pci_try_num: 4
[    0.493888] pci 0000:03:00.0: BAR 6: assigned [mem 0xcd000000-0xcd01ffff pref]
[    0.493891] pci 0000:02:00.0: PCI bridge to [bus 03-03]
[    0.493894] pci 0000:02:00.0:   bridge window [io  0x9000-0x9fff]
[    0.493899] pci 0000:02:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.493902] pci 0000:02:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.493908] pci 0000:02:02.0: PCI bridge to [bus 04-04]
[    0.493917] pci 0000:01:00.0: PCI bridge to [bus 02-04]
[    0.493919] pci 0000:01:00.0:   bridge window [io  0x9000-0x9fff]
[    0.493924] pci 0000:01:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.493927] pci 0000:01:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.493933] pci 0000:00:03.0: PCI bridge to [bus 01-04]
[    0.493935] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.493939] pci 0000:00:03.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.493942] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.493947] pci 0000:00:0f.0: PCI bridge to [bus 05-05]
[    0.493951] pci 0000:00:0f.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.493957] pci 0000:00:13.0: PCI bridge to [bus 06-06]
[    0.493965] pci 0000:00:16.0: PCI bridge to [bus 07-07]
[    0.493969] pci 0000:00:16.0:   bridge window [mem 0xcfd00000-0xcfdfffff]
[    0.493982] pci 0000:00:03.0: setting latency timer to 64
[    0.493988] pci 0000:01:00.0: setting latency timer to 64
[    0.493994] pci 0000:02:00.0: setting latency timer to 64
[    0.494001] pci 0000:02:02.0: setting latency timer to 64
[    0.494007] pci 0000:00:0f.0: setting latency timer to 64
[    0.494013] pci 0000:00:13.0: setting latency timer to 64
[    0.494019] pci 0000:00:16.0: setting latency timer to 64
[    0.494023] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.494025] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.494027] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.494029] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.494032] pci_bus 0000:00: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.494034] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.494037] pci_bus 0000:01: resource 1 [mem 0xca000000-0xcdffffff]
[    0.494040] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.494043] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.494045] pci_bus 0000:02: resource 1 [mem 0xca000000-0xcdffffff]
[    0.494047] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.494049] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.494051] pci_bus 0000:03: resource 1 [mem 0xca000000-0xcdffffff]
[    0.494054] pci_bus 0000:03: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.494056] pci_bus 0000:05: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.494059] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.494062] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.494064] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.494067] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.494070] pci_bus 0000:05: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.494073] pci_bus 0000:07: resource 1 [mem 0xcfd00000-0xcfdfffff]
[    0.494114] NET: Registered protocol family 2
[    0.494260] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.495234] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.498484] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.498995] TCP: Hash tables configured (established 524288 bind 65536)
[    0.498997] TCP reno registered
[    0.499013] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.499053] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.499206] NET: Registered protocol family 1
[    0.499522] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.499546] pci 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[    0.568037] pci 0000:00:0b.0: PCI INT A disabled
[    0.568158] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.568166] pci 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.568191] pci 0000:00:0b.1: PCI INT B disabled
[    0.568360] pci 0000:03:00.0: Boot video device
[    0.568369] PCI: CLS 4 bytes, default 64
[    0.568373] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.568376] Placing 64MB software IO TLB between ffff8800abee9000 - ffff8800afee9000
[    0.568378] software IO TLB at phys 0xabee9000 - 0xafee9000
[    0.568828] audit: initializing netlink socket (disabled)
[    0.568838] type=2000 audit(1348366781.564:1): initialized
[    0.590230] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.592525] VFS: Disk quotas dquot_6.5.2
[    0.592578] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.593095] fuse init (API version 7.17)
[    0.593182] msgmni has been set to 7873
[    0.593744] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.593796] io scheduler noop registered
[    0.593798] io scheduler deadline registered
[    0.593830] io scheduler cfq registered (default)
[    0.593964] pcieport 0000:00:03.0: setting latency timer to 64
[    0.593997] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.594061] pcieport 0000:00:13.0: setting latency timer to 64
[    0.594093] pcieport 0000:00:13.0: irq 41 for MSI/MSI-X
[    0.594155] pcieport 0000:00:16.0: setting latency timer to 64
[    0.594187] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.594363] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.594365] pcieport 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.594367] pcieport 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.594369] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.594371] pcieport 0000:02:02.0: Signaling PME through PCIe PME interrupt
[    0.594375] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.594390] pcieport 0000:00:13.0: Signaling PME through PCIe PME interrupt
[    0.594393] pcie_pme 0000:00:13.0:pcie01: service driver pcie_pme loaded
[    0.594408] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
[    0.594410] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.594413] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
[    0.594431] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.594456] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.594517] intel_idle: MWAIT substates: 0x20
[    0.594519] intel_idle: does not run on family 6 model 15
[    0.594607] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.594612] ACPI: Power Button [PWRB]
[    0.594670] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.594673] ACPI: Power Button [PWRF]
[    0.596425] ERST: Table is not found!
[    0.596428] GHES: HEST is not enabled!
[    0.596550] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.616967] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.617138] Freeing initrd memory: 13864k freed
[    0.888600] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.924442] Linux agpgart interface v0.103
[    0.926532] brd: module loaded
[    0.927633] loop: module loaded
[    0.927882] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.928046] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.928062] pata_acpi 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    0.928077] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.928084] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.928201] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.928209] pata_acpi 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    0.928224] pata_acpi 0000:00:0e.1: setting latency timer to 64
[    0.928231] pata_acpi 0000:00:0e.1: PCI INT B disabled
[    0.928346] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 23
[    0.928350] pata_acpi 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23
[    0.928364] pata_acpi 0000:00:0e.2: setting latency timer to 64
[    0.928371] pata_acpi 0000:00:0e.2: PCI INT C disabled
[    0.928677] Fixed MDIO Bus: probed
[    0.928695] tun: Universal TUN/TAP device driver, 1.6
[    0.928697] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.928782] PPP generic driver version 2.4.2
[    0.928920] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.928946] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.928973] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.928976] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.929067] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.929092] ehci_hcd 0000:00:0b.1: debug port 1
[    0.929099] ehci_hcd 0000:00:0b.1: cache line size of 4 is not supported
[    0.929118] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xcfffe000
[    0.940031] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.940210] hub 1-0:1.0: USB hub found
[    0.940214] hub 1-0:1.0: 10 ports detected
[    0.940301] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.940317] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[    0.940328] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.940330] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.940394] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.940425] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xcffff000
[    0.998157] hub 2-0:1.0: USB hub found
[    0.998163] hub 2-0:1.0: 10 ports detected
[    0.998244] uhci_hcd: USB Universal Host Controller Interface driver
[    0.998295] usbcore: registered new interface driver libusual
[    0.998329] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.998331] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.999027] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.999171] mousedev: PS/2 mouse device common for all mice
[    0.999405] rtc_cmos 00:05: RTC can wake from S4
[    0.999556] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.999587] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.999660] device-mapper: uevent: version 1.0.3
[    0.999757] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.999772] cpuidle: using governor ladder
[    0.999774] cpuidle: using governor menu
[    0.999775] EFI Variables Facility v0.08 2004-May-17
[    1.000031] TCP cubic registered
[    1.000141] NET: Registered protocol family 10
[    1.000665] NET: Registered protocol family 17
[    1.000669] Registering the dns_resolver key type
[    1.000849] PM: Hibernation image not present or could not be loaded.
[    1.000861] registered taskstats version 1
[    1.008002]   Magic number: 12:227:309
[    1.008031] tty tty38: hash matches
[    1.008144] rtc_cmos 00:05: setting system clock to 2012-09-23 02:19:43 UTC (1348366783)
[    1.008181] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.008183] EDD information not available.
[    1.009834] Freeing unused kernel memory: 920k freed
[    1.010140] Write protecting the kernel read-only data: 12288k
[    1.015359] Freeing unused kernel memory: 1616k freed
[    1.017860] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.019715] Freeing unused kernel memory: 1200k freed
[    1.036596] udevd[93]: starting version 175
[    1.071731] sata_nv 0000:00:0e.0: version 3.5
[    1.071750] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    1.071753] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.071986] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.074918] scsi0 : sata_nv
[    1.076701] scsi1 : sata_nv
[    1.076849] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    1.076853] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    1.076922] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    1.076926] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    1.076998] sata_nv 0000:00:0e.1: setting latency timer to 64
[    1.077528] scsi2 : sata_nv
[    1.077628] scsi3 : sata_nv
[    1.077732] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    1.077735] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    1.077763] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 23 (level, low) -> IRQ 23
[    1.077766] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    1.077807] sata_nv 0000:00:0e.2: setting latency timer to 64
[    1.079352] scsi4 : sata_nv
[    1.080283] scsi5 : sata_nv
[    1.080475] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 23
[    1.080479] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 23
[    1.080559] pata_amd 0000:00:0d.0: version 0.4.1
[    1.080623] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.081941] scsi6 : pata_amd
[    1.082091] scsi7 : pata_amd
[    1.082463] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    1.082466] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    1.082492] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.082652] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 22
[    1.082659] forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.082664] forcedeth 0000:00:11.0: setting latency timer to 64
[    1.132073] FDC 0 is a post-1991 82077
[    1.388042] ata3: SATA link down (SStatus 0 SControl 300)
[    1.388047] ata1: SATA link down (SStatus 0 SControl 300)
[    1.504036] usb 2-6: new low-speed USB device number 2 using ohci_hcd
[    1.548055] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.568029] Refined TSC clocksource calibration: 2399.978 MHz.
[    1.568036] Switching to clocksource tsc
[    1.599373] ata5.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    1.599379] ata5.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.604723] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:14:ec:0b
[    1.604726] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.604900] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 21
[    1.604905] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 21 (level, low) -> IRQ 21
[    1.604910] forcedeth 0000:00:12.0: setting latency timer to 64
[    1.666002] ata5.00: configured for UDMA/133
[    1.700030] ata2: SATA link down (SStatus 0 SControl 300)
[    2.128819] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:14:ec:0d
[    2.128823] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    2.168049] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.176152] ata4.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[    2.192164] ata4.00: configured for UDMA/66
[    2.192926] scsi 3:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[    2.195254] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.195258] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.195422] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.195571] sr 3:0:0:0: Attached scsi generic sg0 type 5
[    2.195792] scsi 4:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    2.196038] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.196091] sd 4:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.196218] sd 4:0:0:0: [sda] Write Protect is off
[    2.196221] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.196244] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.213809]  sda: sda1
[    2.214070] sd 4:0:0:0: [sda] Attached SCSI disk
[    2.451131] kjournald starting.  Commit interval 5 seconds
[    2.451219] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    2.508035] ata6: SATA link down (SStatus 0 SControl 300)
[    2.508139] ata8: port disabled--ignoring
[    2.510122] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    2.510134] firewire_ohci 0000:05:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    2.522817] input: Microsoft Microsoft Wireless Optical Mouse\xffffffc2\xffffffae\xffffffae 1.00 as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input3
[    2.523007] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse\xffffffc2\xffffffae\xffffffae 1.00] on usb-0000:00:0b.0-6/input0
[    2.523046] usbcore: registered new interface driver usbhid
[    2.523048] usbhid: USB HID core driver
[    2.564071] firewire_ohci: Added fw-ohci device 0000:05:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.064169] firewire_core: created device fw0: GUID 5ad13ecc00044b16, S400
[   13.376610] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.376616] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.398386] udevd[377]: starting version 175
[   13.436955] i2c i2c-0: nForce2 SMBus adapter at 0xf400
[   13.436984] i2c i2c-1: nForce2 SMBus adapter at 0xf000
[   13.437233] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   13.437333] NV_TCO: Watchdog reboot detected.
[   13.437679] NV_TCO: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   13.440516] lp: driver loaded but no devices found
[   13.545433] cfg80211: Calling CRDA to update world regulatory domain
[   13.555447] EXT3-fs (sda1): using internal journal
[   13.562263] type=1400 audit(1348366796.050:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=592 comm="apparmor_parser"
[   13.562671] type=1400 audit(1348366796.050:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"
[   13.562908] type=1400 audit(1348366796.050:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=592 comm="apparmor_parser"
[   13.564646] type=1400 audit(1348366796.054:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=611 comm="apparmor_parser"
[   13.565053] type=1400 audit(1348366796.054:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=611 comm="apparmor_parser"
[   13.565189] nvidia: module license 'NVIDIA' taints kernel.
[   13.565194] Disabling lock debugging due to kernel taint
[   13.565277] type=1400 audit(1348366796.054:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=611 comm="apparmor_parser"
[   13.566554] type=1400 audit(1348366796.054:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=625 comm="apparmor_parser"
[   13.568458] type=1400 audit(1348366796.058:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=628 comm="apparmor_parser"
[   13.574503] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.574508] Copyright(c) 2003-2011 Intel Corporation
[   13.574836] ACPI: PCI Interrupt Link [AXV7] enabled at IRQ 16
[   13.574871] iwlwifi 0000:07:00.0: PCI INT A -> Link[AXV7] -> GSI 16 (level, low) -> IRQ 16
[   13.574883] iwlwifi 0000:07:00.0: setting latency timer to 64
[   13.574927] iwlwifi 0000:07:00.0: pci_resource_len = 0x00002000
[   13.574929] iwlwifi 0000:07:00.0: pci_resource_base = ffffc9000065c000
[   13.574931] iwlwifi 0000:07:00.0: HW Revision ID = 0x34
[   13.575736] iwlwifi 0000:07:00.0: irq 43 for MSI/MSI-X
[   13.575811] iwlwifi 0000:07:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   13.575876] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   13.590154] iwlwifi 0000:07:00.0: device EEPROM VER=0x715, CALIB=0x6
[   13.590158] iwlwifi 0000:07:00.0: Device SKU: 0X1f0
[   13.590160] iwlwifi 0000:07:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   13.591220] iwlwifi 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.697680] cfg80211: World regulatory domain updated:
[   13.697683] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.697686] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.697688] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.697691] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.697693] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.697696] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.735137] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   13.735143] snd_hda_intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   13.735146] hda_intel: Disabling MSI
[   13.735174] snd_hda_intel 0000:00:0f.1: setting latency timer to 64
[   13.800518] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   13.800525] nvidia 0000:03:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   13.800533] nvidia 0000:03:00.0: setting latency timer to 64
[   13.800539] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.800709] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   13.939151] iwlwifi 0000:07:00.0: loaded firmware version 18.168.6.1
[   13.939795] Registered led device: phy0-led
[   13.939830] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   13.942500] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.008618] init: Failed to spawn samba4 main process: unable to execute: No such file or directory
[   14.014203] init: failsafe main process (871) killed by TERM signal
[   14.097085] Bluetooth: Core ver 2.16
[   14.097168] NET: Registered protocol family 31
[   14.097170] Bluetooth: HCI device and connection manager initialized
[   14.097173] Bluetooth: HCI socket layer initialized
[   14.097175] Bluetooth: L2CAP socket layer initialized
[   14.097182] Bluetooth: SCO socket layer initialized
[   14.099920] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.099923] Bluetooth: BNEP filters: protocol multicast
[   14.103077] Bluetooth: RFCOMM TTY layer initialized
[   14.103082] Bluetooth: RFCOMM socket layer initialized
[   14.103084] Bluetooth: RFCOMM ver 1.11
[   14.128208] type=1400 audit(1348366796.618:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=966 comm="apparmor_parser"
[   14.128674] type=1400 audit(1348366796.618:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=966 comm="apparmor_parser"
[   14.157755] ppdev: user-space parallel port driver
[   14.308919] forcedeth 0000:00:11.0: irq 44 for MSI/MSI-X
[   14.309116] forcedeth 0000:00:11.0: eth0: no link during initialization
[   14.310026] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.310629] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.315877] forcedeth 0000:00:12.0: irq 45 for MSI/MSI-X
[   14.327026] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   14.334382] iwlwifi 0000:07:00.0: Radio type=0x1-0x2-0x0
[   14.340594] init: alsa-restore main process (1040) terminated with status 19
[   14.400041] hda_codec: ALC1200: BIOS auto-probing.
[   15.340244] iwlwifi 0000:07:00.0: Failed to run INIT ucode: -110
[   15.340280] iwlwifi 0000:07:00.0: Unable to initialize device.
[   15.340418] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.349996] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   15.356901] iwlwifi 0000:07:00.0: Radio type=0x1-0x2-0x0
[   15.692152] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
[   15.692269] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   15.692367] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   15.692453] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   15.692540] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   15.692623] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   15.692706] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   15.692789] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input11
[   16.205215] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   16.205218] vesafb: scrolling: redraw
[   16.205221] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.208426] vesafb: framebuffer at 0xcb000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
[   16.209429] Console: switching to colour frame buffer device 80x30
[   16.209444] fb0: VESA VGA frame buffer device
[   20.360028] iwlwifi 0000:07:00.0: Could not load the DATA uCode section
[   20.360257] iwlwifi 0000:07:00.0: Failed to run INIT ucode: -110
[   20.360294] iwlwifi 0000:07:00.0: Unable to initialize device.
[   20.360972] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   20.367873] iwlwifi 0000:07:00.0: Radio type=0x1-0x2-0x0
[   20.371876] do_IRQ: 59 callbacks suppressed
[   20.371880] do_IRQ: 0.153 No irq handler for vector (irq -1)
[   25.368023] iwlwifi 0000:07:00.0: Could not load the INST uCode section
[   25.368244] iwlwifi 0000:07:00.0: Failed to run INIT ucode: -110
[   25.368278] iwlwifi 0000:07:00.0: Unable to initialize device.
[   25.573023] enabling dynamically allocated vcaches
[   25.573027] Starting AFS cache scan...found 1 non-empty cache files (0%).
[   25.921229] init: plymouth-stop pre-start process (1641) terminated with status 1
[   35.920013] eth1: no IPv6 routers present
[   38.940053] usb 1-9: new high-speed USB device number 3 using ehci_hcd
[   40.072405] Initializing USB Mass Storage driver...
[   40.072517] scsi8 : usb-storage 1-9:1.0
[   40.072619] usbcore: registered new interface driver usb-storage
[   40.072621] USB Mass Storage support registered.
[   40.123155] usbcore: registered new interface driver uas
[   41.074499] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2
[   41.075017] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   41.076133] sd 8:0:0:0: [sdb] 2001888 512-byte logical blocks: (1.02 GB/977 MiB)
[   41.078370] sd 8:0:0:0: [sdb] Write Protect is off
[   41.078375] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   41.079361] sd 8:0:0:0: [sdb] No Caching mode page present
[   41.079365] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   41.083358] sd 8:0:0:0: [sdb] No Caching mode page present
[   41.083363] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   41.084137]  sdb: sdb1
[   41.087357] sd 8:0:0:0: [sdb] No Caching mode page present
[   41.087361] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   41.087365] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[   63.413131] sdb: detected capacity change from 1024966656 to 0
[   64.766528] usb 1-9: USB disconnect, device number 3
[  106.700026] usb 1-9: new high-speed USB device number 4 using ehci_hcd
[  106.833405] scsi9 : usb-storage 1-9:1.0
[  107.833927] scsi 9:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[  107.834448] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  107.835051] sd 9:0:0:0: [sdb] 1000944 512-byte logical blocks: (512 MB/488 MiB)
[  107.836428] sd 9:0:0:0: [sdb] Write Protect is off
[  107.836437] sd 9:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  107.837797] sd 9:0:0:0: [sdb] No Caching mode page present
[  107.837801] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  107.841789] sd 9:0:0:0: [sdb] No Caching mode page present
[  107.841794] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  107.842693]  sdb: sdb1 sdb2
[  107.845788] sd 9:0:0:0: [sdb] No Caching mode page present
[  107.845792] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  107.845796] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  108.130528] ISO 9660 Extensions: Microsoft Joliet Level 3
[  108.184622] ISO 9660 Extensions: RRIP_1991A
[  117.258678] sdb: detected capacity change from 512483328 to 0
[  416.944036] usb 1-10: new high-speed USB device number 5 using ehci_hcd
[  417.091052] scsi10 : usb-storage 1-10:1.0
[  418.152198] scsi 10:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 4
[  418.152740] sd 10:0:0:0: Attached scsi generic sg3 type 0
[  419.014113] sd 10:0:0:0: [sdc] 30949376 512-byte logical blocks: (15.8 GB/14.7 GiB)
[  419.017220] sd 10:0:0:0: [sdc] Write Protect is off
[  419.017224] sd 10:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  419.020221] sd 10:0:0:0: [sdc] No Caching mode page present
[  419.020226] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  419.029220] sd 10:0:0:0: [sdc] No Caching mode page present
[  419.029224] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  419.058112]  sdc: unknown partition table
[  419.065221] sd 10:0:0:0: [sdc] No Caching mode page present
[  419.065226] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  419.065229] sd 10:0:0:0: [sdc] Attached SCSI removable disk

```**6 ) Network configuration**
sudo lshw -C network
```

  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 34
       serial: 8c:70:5a:7d:8e:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:cfdfe000-cfdfffff

```**7 ) Scan for networks:**

iwlist scan
```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

```iwlist scan wlan0 (???)
```

iwlist: unknown command `wlan0' (check 'iwlist --help').

```**8 ) Ubuntu Version: **
lsb_release -d
```

Description:    Ubuntu 12.04.1 LTS

```**9 ) Kernel/architecture (including 32 vs. 64 bit): **
uname -mr
```

3.2.0-31-generic x86_64

```**10 ) Restarting the network:**
$ sudo /etc/init.d/networking restart
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

```
I already tried reloading the module, and though there was something fishy with the ucode, so I downloaded a fresh image off of the [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads). MD5 sums match against what is provided with ubuntu.

Any ideas ?

---

### Post by GeoPirate on 2012-09-28
I have a couple of these cards coming in the mail, I will let you know if I run into similar issues.

---

