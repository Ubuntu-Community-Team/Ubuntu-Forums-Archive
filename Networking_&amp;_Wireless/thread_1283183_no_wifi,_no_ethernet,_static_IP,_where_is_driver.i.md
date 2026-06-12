---
title: "no wifi, no ethernet, static IP, where is driver.inf, what is the problem ?"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by francoise_peace on 2009-10-05
Hello, no wifi and no ethernet, static IP.
 I’ve installed Ndiswrapper: [http://doc.ubuntu-fr.org/ndisgtk](http://doc.ubuntu-fr.org/ndisgtk)
 But I don’t know how to obtain driver.inf.
Thanks a lot !

 

 **francoise@Charmmy-Kitty:~$ cat /etc/lsb-release** 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=9.04 
 DISTRIB_CODENAME=jaunty 
 DISTRIB_DESCRIPTION="Ubuntu 9.04" 
 **francoise@Charmmy-Kitty:~$ lsusb **
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device 
 **francoise@Charmmy-Kitty:~$ lspci **
 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
 00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 
 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
 **francoise@Charmmy-Kitty:~$ sudo lshw -C network** 
 [sudo] password for francoise:  
   *-network                
        description: Ethernet interface 
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        logical name: eth0 
        version: 02 
        serial: 00:1f:16:4d:38:d5 
        size: 100MB/s 
        capacity: 100MB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s 
   *-network DISABLED 
        description: Ethernet interface 
        physical id: 1 
        logical name: pan0 
        serial: 5e:c3:23:ac:09:44 
        capabilities: ethernet physical 
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
 **francoise@Charmmy-Kitty:~$ lsmod **
 Module                  Size  Used by 
 i915                   67844  2  
 drm                    96424  3 i915 
 binfmt_misc            16776  1  
 ppdev                  15620  0  
 bridge                 56212  0  
 stp                    10500  1 bridge 
 bnep                   20224  2  
 vboxnetflt             91016  0  
 vboxdrv               117672  1 vboxnetflt 
 input_polldev          11912  0  
 ipt_REJECT             11136  1  
 ipt_LOG                13700  1  
 xt_limit               10116  2  
 xt_tcpudp              11008  7  
 xt_state               10112  5  
 ipt_addrtype           10496  4  
 ip6table_filter        10624  1  
 ip6_tables             20880  1 ip6table_filter 
 nf_nat_irc             10240  0  
 nf_conntrack_irc       13220  1 nf_nat_irc 
 nf_nat_ftp             10752  0  
 nf_nat                 25876  2 nf_nat_irc,nf_nat_ftp 
 nf_conntrack_ipv4      21388  7 nf_nat 
 nf_defrag_ipv4          9984  1 nf_conntrack_ipv4 
 nf_conntrack_ftp       15652  1 nf_nat_ftp 
 nf_conntrack           72008  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp 
 iptable_filter         10752  1  
 ip_tables              19600  1 iptable_filter 
 x_tables               23044  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables 
 joydev                 18368  0  
 lp                     17156  0  
 parport                42220  2 ppdev,lp 
 snd_hda_intel         435252  2  
 snd_pcm_oss            46336  0  
 snd_mixer_oss          22656  1 snd_pcm_oss 
 snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss 
 snd_seq_dummy          10756  0  
 snd_seq_oss            37760  0  
 snd_seq_midi           14336  0  
 snd_rawmidi            29696  1 snd_seq_midi 
 snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
 snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 snd_timer              29704  2 snd_pcm,snd_seq 
 snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 uvcvideo               63368  0  
 snd                    62756  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              15200  1 snd 
 compat_ioctl32          9344  1 uvcvideo 
 psmouse                61972  0  
 snd_page_alloc         16904  2 snd_hda_intel,snd_pcm 
 videodev               41600  1 uvcvideo 
 v4l1_compat            21764  2 uvcvideo,videodev 
 pcspkr                 10496  0  
 video                  25872  0  
 serio_raw              13444  0  
 intel_agp              34108  1  
 agpgart                42696  3 drm,intel_agp 
 iTCO_wdt               19108  0  
 iTCO_vendor_support    11652  1 iTCO_wdt 
 output                 11008  1 video 
 ath_pci                99224  0  
 wlan                  210544  1 ath_pci 
 ath_hal               198864  1 ath_pci 
 r8169                  40836  0  
 mii                    13312  1 r8169 
 usb_storage            99648  0  
 fbcon                  46112  0  
 tileblit               10752  1 fbcon 
 font                   16384  1 fbcon 
 bitblit                13824  1 fbcon 
 softcursor              9984  1 bitblit 
 **francoise@Charmmy-Kitty:~$ iwconfig **
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 pan0      no wireless extensions. 
  
 **francoise@Charmmy-Kitty:~$ ifconfig **
 eth0      Link encap:Ethernet  HWaddr 00:1f:16:4d:38:d5   
           inet adr:192.168.1.2  Bcast:192.168.1.255  Masque:255.255.255.0 
           adr inet6: fe80::21f:16ff:fe4d:38d5/64 Scope:Lien 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           Packets reçus:11034 erreurs:0 :0 overruns:0 frame:0 
           TX packets:10859 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 lg file transmission:1000  
           Octets reçus:7529357 (7.5 MB) Octets transmis:2404054 (2.4 MB) 
           Interruption:252 Adresse de base:0xa000  
  
 lo        Link encap:Boucle locale   
           inet adr:127.0.0.1  Masque:255.0.0.0 
           adr inet6: ::1/128 Scope:Hôte 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           Packets reçus:72 erreurs:0 :0 overruns:0 frame:0 
           TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 lg file transmission:0  
           Octets reçus:10283 (10.2 KB) Octets transmis:10283 (10.2 KB) 
  
 **francoise@Charmmy-Kitty:~$ sudo iwlist scan** 
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 pan0      Interface doesn't support scanning. 
  
 **francoise@Charmmy-Kitty:~$ uname -r -m **
 2.6.28-15-generic i686 
 **francoise@Charmmy-Kitty:~$ cat  /etc/network/interfaces** 
 auto eth0 
 iface eth0 inet static 
 address 192.168.1.2 
 netmask 255.255.255.0 
 gateway 192.168.1.1 
  
 auto lo 
 iface lo inet loopback 
  
 **francoise@Charmmy-Kitty:~$ nm-tool **
  
 NetworkManager Tool 
  
 State: connected 
  
 - Device: eth0 ----------------------------------------------------------------- 
   Type:              Wired 
   Driver:            r8169 
   State:             unmanaged 
   Default:           no 
   HW Address:        00:00:00:00:00:00 
  
   Capabilities: 
     Carrier Detect:  yes 
     Speed:           100 Mb/s 
  
   Wired Properties 
     Carrier:         on 
  
 **francoise@Charmmy-Kitty:~$ lspci | grep -i net **
 01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
 francoise@Charmmy-Kitty:~$

---

### Post by bkratz on 2009-10-05
Maybe I just missed it, but I don't see a wireless card listed in any of your outputs. Could it maybe turned off in the bios?

---

### Post by urugTON on 2009-10-05
I'm a little confused by your headline.  In particular "no ethernet, static IP" part.  The eth0 interface is set up as static.  It looks as though eth0 is up and running since it has handled about 20,000 packets.  I don't see anything in /etc/network/interfaces that would cause the wireless interface to have a static IP.

Perhaps you could clear up my confusion.

With regards to the wireless:

Please do as bkratz suggested.  Check your BIOS.  My BIOS has a entry WLAN: Enable/Disable.  When I select Disable, my wireless card disappears from dmesg, lspci and so on.  As a matter of fact, it looks very similar to what you have.

If the BIOS is not the problem, then how about some more information?

What kind of computer do you have: laptop/desktop, manufacturer, model and so on.  What wireless card do you have?  What led you to install NDIS?

---

### Post by francoise_peace on 2009-10-06
Hello, I don't know how to check and modify the BIOS ?

The idea of ndiswrapper came out of: [http://doc.ubuntu-fr.org/wifi_liste_carte#r](http://doc.ubuntu-fr.org/wifi_liste_carte#r)

Even if my card is: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller.

My pc is a COMPAQ Presario CQ70-105EF

What I can tell you about my bios is that:

 francoise@Charmmy-Kitty:~$ sudo dmidecode
[sudo] password for francoise: 
# dmidecode 2.9
SMBIOS 2.4 present.
33 structures occupying 1565 bytes.
Table at 0x000E51A0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.26
    Release Date: 10/01/2008
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: Compaq Presario CQ70 Notebook PC
    Version: F.26
    Serial Number: 2CE8451MBW
    UUID: E95B79A0-B0E3-11DD-BEC9-84FAD2957ECE
    Wake-up Type: Power Switch
    SKU Number: FR341EA#ABF
    Family: 103C_5335KV

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
    Manufacturer: Wistron
    Product Name: 360C
    Version: 09.45
    Serial Number: 2CE8451MBW
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer: Wistron
    Type: Notebook
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Chassis Asset Tag
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x0000010D
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: Available
    Length: Other
    ID: 0
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0005, DMI type 9, 13 bytes
System Slot Information
    Designation: J6B1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Other
    ID: 0
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0006, DMI type 9, 13 bytes
System Slot Information
    Designation: J6C2
    Type: x1 PCI Express
    Current Usage: Available
    Length: Other
    ID: 1
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
    Designation: J7B1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Other
    ID: 2
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0008, DMI type 9, 13 bytes
System Slot Information
    Designation: J8B3
    Type: x1 PCI Express
    Current Usage: Available
    Length: Other
    ID: 3
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0009, DMI type 9, 13 bytes
System Slot Information
    Designation: J8D1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Other
    ID: 4
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description: Video Graphics Controller

Handle 0x000B, DMI type 11, 5 bytes
OEM Strings
    String 1: $HP$
    String 2: ABS 70/71 79 7A 7B 7C
    String 3: LOC#ABF
    String 4: String4 for Original Equipment Manufacturer
    String 5: String5 for Original Equipment Manufacturer

Handle 0x000C, DMI type 12, 5 bytes
System Configuration Options
    Option 1: String1 for Type12 Equipment Manufacturer
    Option 2: String2 for Type12 Equipment Manufacturer
    Option 3: String3 for Type12 Equipment Manufacturer
    Option 4: String4 for Type12 Equipment Manufacturer

Handle 0x000D, DMI type 15, 29 bytes
System Event Log
    Area Length: 32672 bytes
    Header Start Offset: 0x0000
    Data Start Offset: 0x0000
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0000
    Status: Valid, Not Full
    Change Token: 0x12345678
    Header Format: OEM-specific
    Supported Log Type Descriptors: 3
    Descriptor 1: POST memory resize
    Data Format 1: None
    Descriptor 2: POST error
    Data Format 2: POST results bitmap
    Descriptor 3: Log area reset/cleared
    Data Format 3: None

Handle 0x000E, DMI type 21, 7 bytes
Built-in Pointing Device
    Type: Touch Pad
    Interface: PS/2
    Buttons: 4

Handle 0x000F, DMI type 27, 14 bytes
Cooling Device
    Type: Fan
    Status: OK
    OEM-specific Information: 0x00000000
    Nominal Speed: 43690 rpm

Handle 0x0010, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0011, DMI type 39, 22 bytes
System Power Supply
    Location: OEM_Define0
    Name: OEM_Define1
    Manufacturer: OEM_Define2
    Serial Number: OEM_Define2
    Asset Tag: OEM_Define3
    Model Part Number: OEM_Define4
    Revision: OEM_Define5
    Max Power Capacity: 0.075 W
    Status: Present, OK
    Type: Regulator
    Input Voltage Range Switching: Auto-switch
    Plugged: No
    Hot Replaceable: No

Handle 0x0012, DMI type 129, 5 bytes
OEM-specific Type
    Header and Data:
        81 05 12 00 4F
    Strings:
        em Test 1
        Oem Test 2

Handle 0x0013, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: No Error
    Number Of Devices: 2

Handle 0x0014, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: 0x0015
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F7F7F43000000
    Serial Number: 00000000
    Asset Tag: Unknown
    Part Number: RMN1150EC48D7F-667

Handle 0x0015, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0016, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0014
    Memory Array Mapped Address Handle: 0x001B
    Partition Row Position: 1
    Interleave Position: 1
    Interleaved Data Depth: 1

Handle 0x0017, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0013
    Error Information Handle: 0x0018
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK 2
    Type: DDR2
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F7F7F43000000
    Serial Number: 00000000
    Asset Tag: Unknown
    Part Number: RMN1150EC48D7F-667

Handle 0x0018, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0019, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0017
    Memory Array Mapped Address Handle: 0x001B
    Partition Row Position: 2
    Interleave Position: 2
    Interleaved Data Depth: 1

Handle 0x001A, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x001B, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x0013
    Partition Width: 0

Handle 0x001C, DMI type 4, 35 bytes
Processor Information
    Socket Designation: CPU
    Type: Central Processor
    Family: Pentium M
    Manufacturer: Intel(R) Corporation
    ID: FD 06 00 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 15, Stepping 13
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
    Version: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
    Voltage: 1.6 V
    External Clock: 667 MHz
    Max Speed: 2000 MHz
    Current Speed: 1000 MHz
    Status: Populated, Enabled
    Upgrade: <OUT OF SPEC>
    L1 Cache Handle: 0x001F
    L2 Cache Handle: 0x001D
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: FFFF
    Part Number: Not Specified

Handle 0x001D, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x001E, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 8-way Set-associative

Handle 0x001F, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0020, DMI type 127, 4 bytes
End Of Table

francoise@Charmmy-Kitty:~$

---

### Post by directhex on 2009-10-06
> **francoise_peace said:**
> Hello, I don't know how to check and modify the BIOS ?

The idea of ndiswrapper came out of: [http://doc.ubuntu-fr.org/wifi_liste_carte#r](http://doc.ubuntu-fr.org/wifi_liste_carte#r)

Even if my card is: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller.

The 8101E is a wired network card - not WiFi. That's the point people are making - no wireless chip is being detected at all (it would be shown in lspci or lsusb if it were, even if there were no drivers)

Check to see if you've accidentally flipped some kind of "wireless disable" switch on the laptop - mine has one, for use on airplanes where WiFi is banned

---

### Post by francoise_peace on 2009-10-06
OK so, I logged in BIOS (with ESC), but there was no where where WLAN was written although it is in english (I am in french Ubuntu but I can change language if necessary).

So I don't think my BIOS control WLAN or you must specify me better how to find it.

Yes I have a button, but since I changed from Vista to Ubuntu it became red all the time.
Usually it is blue for WIFI on and red for WIFI off. And it doesn't obey any more although it is quite new, my pc is less than 1year old, but since format disk, no more guarantee, the fabricant HP Compaq told me: no Windows GTH in the french polite way.

So I couldn't solve the red button problem with Compaq. So I think at first button was on then it became off, so how to control it, if pressing it = no result ?

---

