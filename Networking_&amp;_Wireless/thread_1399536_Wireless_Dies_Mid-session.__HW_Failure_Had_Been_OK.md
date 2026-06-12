---
title: "Wireless Dies Mid-session.  HW Failure? Had Been OK Under 8.10/9.04/9.10"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Peter108 on 2010-02-05
Synopsis:
A couple of years ago, I had someone blow Vista off my laptop and replace it w/ 8.10.  Wireless worked fine.  Upgraded to 9.04.  Again, wireless worked out of the box.  Upgraded to 9.10.  After maybe an extra reboot or two, wireless again worked fine w/ no tweaking on my part.  A few weeks ago, wireless died mid-session.  Consecutive reboots did not help.  Oddly, dropping down to hibernation and resuming did work.  Then, finally wireless again died mid-session and I have not been able to resuscitate it since.  I smell hardware failure.  I'm afraid I didn't use grep to screen for wlan info  b/c I don't know what that is.  I do know I'm running with a Broadcomm chipset.  I've reset my router, to no effect.  Double-checked the physical wireless switch.  When operable, a blue light would display next to the switch.  Now it's yellow, and has remained that way since my wireless went belly up.  Diagnostics follow:

**1 ) Machine Brand and Model (PC/Laptop): Compaq/HP F572US**
**2 ) Wireless Brand, Model and Wireless Chipset: No information (that I can detect) returned re Wireless Brand/chipset**
```
peter@peter-laptop:~$ lspci 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2) 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3) 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) 
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
peter@peter-laptop:~$ lsusb 
Bus 002 Device 003: ID 03f0:7804 Hewlett-Packard DeskJet D1360 
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
peter@peter-laptop:~$ 
```
**3) Check interface**
```
peter@peter-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions
```. 

```
peter@peter-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:36:ee:7f:8a  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:36ff:feee:7f8a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:13584 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12522 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:10987735 (10.9 MB)  TX bytes:2536888 (2.5 MB) 
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:8769 (8.7 KB)  TX bytes:8769 (8.7 KB) 

peter@peter-laptop:~$ 
```

**4) lsmod**
```
peter@peter-laptop:~$ lsmod (I don't know my “wlan_module_name” so didn't know what to grep for)
Module                  Size  Used by 
isofs                  31620  0 
udf                    80900  1 
crc_itu_t               1852  1 udf 
usblp                  12636  0 
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep               7200  1 snd_hda_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi 
ip_tables              11692  1 iptable_filter 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi 
joydev                 10240  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              22276  2 snd_pcm,snd_seq 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
x_tables               16544  1 ip_tables 
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7264  1 snd 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm 
i2c_nforce2             6784  0 
k8temp                  4188  0 
psmouse                56500  0 
lp                      8964  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp 
usbhid                 38208  0 
forcedeth              54152  0 
video                  19380  0 
output                  2780  1 video 
usb_storage            52576  0 
```
**5) dmesg (again, didn't know what to grep for, so unfortunately output is lengthy)**

```
[    0.003765] ... generic counters:        4
[    0.003768] ... value mask:              0000ffffffffffff
[    0.003770] ... max period:              00007fffffffffff
[    0.003773] ... fixed-purpose counters:  0
[    0.003775] ... counter mask:            000000000000000f
[    0.003780] Checking 'hlt' instruction... OK.
[    0.018532] ACPI: Core revision 20090521
[    0.032620] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074586] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3415.57 BogoMIPS (lpj=6831155)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.160525] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.160557] Brought up 2 CPUs
[    0.160561] Total of 2 processors activated (6830.66 BogoMIPS).
[    0.160555] System has AMD C1E enabled
[    0.160555] Switch to broadcast mode on CPU1
[    0.160680] CPU0 attaching sched-domain:
[    0.160684]  domain 0: span 0-1 level MC
[    0.160687]   groups: 0 1
[    0.160695] CPU1 attaching sched-domain:
[    0.160697]  domain 0: span 0-1 level MC
[    0.160700]   groups: 1 0
[    0.160791] Switch to broadcast mode on CPU0
[    0.160791] Booting paravirtualized kernel on bare hardware
[    0.160791] regulator: core version 0.5
[    0.160791] Time:  9:56:50  Date: 02/04/10
[    0.160791] NET: Registered protocol family 16
[    0.160791] EISA bus registered
[    0.160791] ACPI: bus type pci registered
[    0.160791] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.160791] PCI: MCFG area at e0000000 reserved in E820
[    0.160791] PCI: Using MMCONFIG for extended config space
[    0.160791] PCI: Using configuration type 1 for base access
[    0.161556] bio: create slab <bio-0> at 0
[    0.161556] ACPI: EC: Look up EC in DSDT
[    0.165998] ACPI: BIOS _OSI(Linux) query ignored
[    0.166403] ACPI: Interpreter enabled
[    0.166409] ACPI: (supports S0 S3 S4 S5)
[    0.166433] ACPI: Using IOAPIC for interrupt routing
[    0.164026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.182802] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.182806] ACPI: EC: driver started in interrupt mode
[    0.183088] ACPI: No dock devices found.
[    0.183216] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.183510] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183514] pci 0000:00:02.0: PME# disabled
[    0.183551] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183555] pci 0000:00:03.0: PME# disabled
[    0.183578] pci 0000:00:05.0: reg 10 32bit mmio: [0xb2000000-0xb2ffffff]
[    0.183585] pci 0000:00:05.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.183592] pci 0000:00:05.0: reg 1c 64bit mmio: [0xb1000000-0xb1ffffff]
[    0.183598] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.183789] pci 0000:00:0a.0: reg 10 io port: [0x1d00-0x1d7f]
[    0.183854] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.183860] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.183886] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.183892] pci 0000:00:0a.1: PME# disabled
[    0.183928] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.184034] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.184065] pci 0000:00:0b.0: supports D1 D2
[    0.184068] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184072] pci 0000:00:0b.0: PME# disabled
[    0.184103] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.184137] pci 0000:00:0b.1: supports D1 D2
[    0.184139] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184144] pci 0000:00:0b.1: PME# disabled
[    0.184185] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.184232] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.184238] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.184243] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.184249] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.184255] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.184261] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]
[    0.184355] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.184392] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.184397] pci 0000:00:10.1: PME# disabled
[    0.184433] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]
[    0.184439] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.184464] pci 0000:00:14.0: supports D1 D2
[    0.184467] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184471] pci 0000:00:14.0: PME# disabled
[    0.184605] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.184609] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb7ffffff]
[    0.184614] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.184656] pci 0000:00:03.0: bridge io port: [0x5000-0x5fff]
[    0.184660] pci 0000:00:03.0: bridge 32bit mmio: [0xb8000000-0xbbffffff]
[    0.184665] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0200000-0xd03fffff]
[    0.184706] pci 0000:00:10.0: transparent bridge
[    0.184719] pci_bus 0000:00: on NUMA node 0
[    0.184723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.184885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.184924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.219831] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.220053] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.220254] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.220454] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.220656] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.220858] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.221059] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.221261] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.221463] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.221664] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.221867] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.222080] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.222282] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.222484] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.222687] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.222890] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.223092] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.223304] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.223511] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.223747] SCSI subsystem initialized
[    0.224035] libata version 3.00 loaded.
[    0.224064] usbcore: registered new interface driver usbfs
[    0.224064] usbcore: registered new interface driver hub
[    0.228016] usbcore: registered new device driver usb
[    0.228105] ACPI: WMI: Mapper loaded
[    0.228108] PCI: Using ACPI for IRQ routing
[    0.236011] Bluetooth: Core ver 2.15
[    0.240016] NET: Registered protocol family 31
[    0.240019] Bluetooth: HCI device and connection manager initialized
[    0.240023] Bluetooth: HCI socket layer initialized
[    0.240026] NetLabel: Initializing
[    0.240028] NetLabel:  domain hash size = 128
[    0.240030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.240048] NetLabel:  unlabeled traffic allowed by default
[    0.240095] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.240102] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.252028] Switched to high resolution mode on CPU 0
[    0.252044] Switched to high resolution mode on CPU 1
[    0.257050] pnp: PnP ACPI init
[    0.257073] ACPI: bus type pnp registered
[    0.260309] pnp: PnP ACPI: found 13 devices
[    0.260313] ACPI: ACPI bus type pnp unregistered
[    0.260317] PnPBIOS: Disabled by ACPI PNP
[    0.260331] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.260338] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.260343] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.260347] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.260351] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.260358] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.260369] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.260372] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.260376] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.260380] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.260384] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.260387] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.260391] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.260398] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.260402] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.260406] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.295106] AppArmor: AppArmor Filesystem Enabled
[    0.295153] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.295157] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.295161] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb7ffffff
[    0.295165] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.295170] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.295174] pci 0000:00:03.0:   IO window: 0x5000-0x5fff
[    0.295178] pci 0000:00:03.0:   MEM window: 0xb8000000-0xbbffffff
[    0.295182] pci 0000:00:03.0:   PREFETCH window: 0x000000d0200000-0x000000d03fffff
[    0.295187] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.295189] pci 0000:00:10.0:   IO window: disabled
[    0.295194] pci 0000:00:10.0:   MEM window: disabled
[    0.295197] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.295208] pci 0000:00:02.0: setting latency timer to 64
[    0.295214] pci 0000:00:03.0: setting latency timer to 64
[    0.295220] pci 0000:00:10.0: setting latency timer to 64
[    0.295225] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.295228] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.295232] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.295235] pci_bus 0000:01: resource 1 mem: [0xb4000000-0xb7ffffff]
[    0.295239] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd01fffff]
[    0.295243] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    0.295246] pci_bus 0000:03: resource 1 mem: [0xb8000000-0xbbffffff]
[    0.295249] pci_bus 0000:03: resource 2 pref mem [0xd0200000-0xd03fffff]
[    0.295253] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.295256] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]
[    0.295302] NET: Registered protocol family 2
[    0.295420] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.295824] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.296732] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.297198] TCP: Hash tables configured (established 131072 bind 65536)
[    0.297202] TCP reno registered
[    0.297321] NET: Registered protocol family 1
[    0.297407] Trying to unpack rootfs image as initramfs...
[    0.542127] Freeing initrd memory: 7461k freed
[    0.547970] Simple Boot Flag at 0x36 set to 0x1
[    0.548205] cpufreq-nforce2: No nForce2 chipset.
[    0.548237] Scanning for low memory corruption every 60 seconds
[    0.548358] audit: initializing netlink socket (disabled)
[    0.548376] type=2000 audit(1265277409.545:1): initialized
[    0.559142] highmem bounce pool size: 64 pages
[    0.559149] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.560862] VFS: Disk quotas dquot_6.5.2
[    0.560933] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.561602] fuse init (API version 7.12)
[    0.561695] msgmni has been set to 1707
[    0.562035] alg: No test for stdrng (krng)
[    0.562054] io scheduler noop registered
[    0.562057] io scheduler anticipatory registered
[    0.562059] io scheduler deadline registered
[    0.562109] io scheduler cfq registered (default)
[    0.562138] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.562144] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.562187] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.562214] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.562221] pci 0000:00:05.0: Boot video device
[    0.764660] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.764717] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.764775] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.764907]   alloc irq_desc for 24 on node -1
[    0.764911]   alloc kstat_irqs on node -1
[    0.764922] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.764928] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.765026]   alloc irq_desc for 25 on node -1
[    0.765029]   alloc kstat_irqs on node -1
[    0.765034] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.765039] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.765112] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.765142] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.766620] ACPI: AC Adapter [ACAD] (on-line)
[    0.766717] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.766722] ACPI: Power Button [PWRF]
[    0.766777] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.766781] ACPI: Power Button [PWRB]
[    0.766831] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.766834] ACPI: Sleep Button [SLPB]
[    0.766887] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.767619] ACPI: Lid Switch [LID]
[    0.767933] ACPI: processor limited to max C-state 1
[    0.767969] processor LNXCPU:00: registered as cooling_device0
[    0.768017] processor LNXCPU:01: registered as cooling_device1
[    0.773111] thermal LNXTHERM:01: registered as thermal_zone0
[    0.773121] ACPI: Thermal Zone [THRM] (58 C)
[    0.773195] isapnp: Scanning for PnP cards...
[    1.052801] ACPI: Battery Slot [BAT0] (battery present)
[    1.126187] isapnp: No Plug & Play device found
[    1.127647] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.129135] brd: module loaded
[    1.129681] loop: module loaded
[    1.129783] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.130054] sata_nv 0000:00:0e.0: version 3.5
[    1.130067] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    1.130428] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    1.130435]   alloc irq_desc for 23 on node -1
[    1.130438]   alloc kstat_irqs on node -1
[    1.130451] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.130455] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.130513] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.130713] scsi0 : sata_nv
[    1.130857] scsi1 : sata_nv
[    1.131038] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    1.131043] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    1.131168] pata_amd 0000:00:0d.0: version 0.4.1
[    1.131214] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.131309] scsi2 : pata_amd
[    1.131389] scsi3 : pata_amd
[    1.132075] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.132079] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.132919] Fixed MDIO Bus: probed
[    1.132959] PPP generic driver version 2.4.2
[    1.133099] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.133451] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.133457]   alloc irq_desc for 22 on node -1
[    1.133460]   alloc kstat_irqs on node -1
[    1.133472] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    1.133491] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.133495] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.133555] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.133588] ehci_hcd 0000:00:0b.1: debug port 1
[    1.133594] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.133618] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    1.144037] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.144135] usb usb1: configuration #1 chosen from 1 choice
[    1.144171] hub 1-0:1.0: USB hub found
[    1.144181] hub 1-0:1.0: 8 ports detected
[    1.144254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.144612] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    1.144617]   alloc irq_desc for 21 on node -1
[    1.144620]   alloc kstat_irqs on node -1
[    1.144630] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, high) -> IRQ 21
[    1.144644] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.144648] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.144688] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.144721] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xb0004000
[    1.202093] usb usb2: configuration #1 chosen from 1 choice
[    1.202127] hub 2-0:1.0: USB hub found
[    1.202138] hub 2-0:1.0: 8 ports detected
[    1.202218] uhci_hcd: USB Universal Host Controller Interface driver
[    1.202324] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.216392] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.216401] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.216484] mice: PS/2 mouse device common for all mice
[    1.216646] rtc_cmos 00:09: RTC can wake from S4
[    1.216684] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.216722] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.216844] device-mapper: uevent: version 1.0.3
[    1.216968] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.217062] device-mapper: multipath: version 1.1.0 loaded
[    1.217066] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.217210] EISA: Probing bus 0 at eisa.0
[    1.217217] Cannot allocate resource for EISA slot 1
[    1.217220] Cannot allocate resource for EISA slot 2
[    1.217222] Cannot allocate resource for EISA slot 3
[    1.217225] Cannot allocate resource for EISA slot 4
[    1.217228] Cannot allocate resource for EISA slot 5
[    1.217239] EISA: Detected 0 cards.
[    1.217317] cpuidle: using governor ladder
[    1.217320] cpuidle: using governor menu
[    1.217921] TCP cubic registered
[    1.218115] NET: Registered protocol family 10
[    1.218633] lo: Disabled Privacy Extensions
[    1.219006] NET: Registered protocol family 17
[    1.219032] Bluetooth: L2CAP ver 2.13
[    1.219035] Bluetooth: L2CAP socket layer initialized
[    1.219038] Bluetooth: SCO (Voice Link) ver 0.6
[    1.219040] Bluetooth: SCO socket layer initialized
[    1.219090] Bluetooth: RFCOMM TTY layer initialized
[    1.219093] Bluetooth: RFCOMM socket layer initialized
[    1.219096] Bluetooth: RFCOMM ver 1.11
[    1.219126] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)
[    1.219176] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13
[    1.219179] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[    1.219182] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[    1.219275] Using IPI No-Shortcut mode
[    1.219377] PM: Resume from disk failed.
[    1.219392] registered taskstats version 1
[    1.219540]   Magic number: 14:118:929
[    1.219664] rtc_cmos 00:09: setting system clock to 2010-02-04 09:56:51 UTC (1265277411)
[    1.219668] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.219670] EDD information not available.
[    1.227494] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.296343] ata3.00: ATAPI: Optiarc DVD RW AD-7530A, EH31, max MWDMA2
[    1.296372] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[    1.312289] ata3.00: configured for MWDMA2
[    1.512053] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.596078] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.604403] ata1.00: ATA-8: Hitachi HTS545032B9A300, PB3OC64G, max UDMA/133
[    1.604408] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.620435] ata1.00: configured for UDMA/133
[    1.620573] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54503 PB3O PQ: 0 ANSI: 5
[    1.620733] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.620777] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.620828] sd 0:0:0:0: [sda] Write Protect is off
[    1.620831] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.620857] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.620994]  sda:
[    1.647972] usb 1-6: configuration #1 chosen from 1 choice
[    1.942559] ata2: SATA link down (SStatus 0 SControl 300)
[    1.943944] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EH31 PQ: 0 ANSI: 5
[    1.952054] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.953143] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.953146] Uniform CD-ROM driver Revision: 3.20
[    1.953251] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.953314] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.953364] ata4: port disabled. ignoring.
[    1.954244]  sda1 sda2 < sda5 sda6 >
[    1.998282] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.998308] Freeing unused kernel memory: 540k freed
[    1.998823] Write protecting the kernel text: 4568k
[    1.998869] Write protecting the kernel read-only data: 1836k
[    2.193218] usb 2-2: configuration #1 chosen from 1 choice
[    2.211111] Initializing USB Mass Storage driver...
[    2.211378] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.211483] usbcore: registered new interface driver usb-storage
[    2.211491] USB Mass Storage support registered.
[    2.211599] usb-storage: device found at 3
[    2.211601] usb-storage: waiting for device to settle before scanning
[    2.230513] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.230890] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.230896]   alloc irq_desc for 20 on node -1
[    2.230900]   alloc kstat_irqs on node -1
[    2.230913] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    2.230919] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.230965] nv_probe: set workaround bit for reversed mac addr
[    2.274560] acpi device:24: registered as cooling_device2
[    2.274786] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input6
[    2.274860] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[    2.286637] usbcore: registered new interface driver hiddev
[    2.293401] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input7
[    2.293494] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-2/input0
[    2.293516] usbcore: registered new interface driver usbhid
[    2.293520] usbhid: v2.6:USB HID core driver
[    2.749225] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:ee:7f:8a
[    2.749232] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    3.515283] PM: Starting manual resume from disk
[    3.515289] PM: Resume from partition 8:6
[    3.515292] PM: Checking hibernation image.
[    3.515469] PM: Resume from disk failed.
[    3.521069] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.521076] EXT4-fs (sda5): write access will be enabled during recovery
[    3.534272] EXT4-fs (sda5): barriers enabled
[    5.109695] kjournald2 starting: pid 382, dev sda5:8, commit interval 5 seconds
[    5.109733] EXT4-fs (sda5): delayed allocation enabled
[    5.109738] EXT4-fs: file extents enabled
[    5.136417] EXT4-fs: mballoc enabled
[    5.136439] EXT4-fs (sda5): orphan cleanup on readonly fs
[    5.136451] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1150
[    5.136607] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262556
[    5.136687] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262552
[    5.136709] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262547
[    5.136728] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262543
[    5.136748] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262539
[    5.136813] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262537
[    5.136834] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262526
[    5.136894] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 521
[    5.136915] EXT4-fs (sda5): 9 orphan inodes deleted
[    5.136919] EXT4-fs (sda5): recovery complete
[    5.334137] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.859319] type=1505 audit(1265277416.138:2): operation="profile_load" pid=405 name=/usr/share/gdm/guest-session/Xsession
[    5.862076] type=1505 audit(1265277416.140:3): operation="profile_load" pid=406 name=/sbin/dhclient3
[    5.862429] type=1505 audit(1265277416.140:4): operation="profile_load" pid=406 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.862626] type=1505 audit(1265277416.140:5): operation="profile_load" pid=406 name=/usr/lib/connman/scripts/dhclient-script
[    5.903424] type=1505 audit(1265277416.181:6): operation="profile_load" pid=407 name=/usr/bin/evince
[    5.909204] type=1505 audit(1265277416.189:7): operation="profile_load" pid=407 name=/usr/bin/evince-previewer
[    5.912672] type=1505 audit(1265277416.189:8): operation="profile_load" pid=407 name=/usr/bin/evince-thumbnailer
[    5.931311] type=1505 audit(1265277416.209:9): operation="profile_load" pid=409 name=/usr/lib/cups/backend/cups-pdf
[    5.931742] type=1505 audit(1265277416.209:10): operation="profile_load" pid=409 name=/usr/sbin/cupsd
[    5.945293] type=1505 audit(1265277416.225:11): operation="profile_load" pid=410 name=/usr/sbin/tcpdump
[    6.837657] Adding 5847620k swap on /dev/sda6.  Priority:-1 extents:1 across:5847620k 
[    7.105191] EXT4-fs (sda5): internal journal on sda5:8
[    7.208235] usb-storage: device scan complete
[    7.209930] scsi 4:0:0:0: Direct-Access     HP       v100w            1.00 PQ: 0 ANSI: 2
[    7.210397] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    7.211046] sd 4:0:0:0: [sdb] 15654848 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    7.211778] sd 4:0:0:0: [sdb] Write Protect is off
[    7.211781] sd 4:0:0:0: [sdb] Mode Sense: 32 07 03 f0
[    7.211784] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.214791] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.214796]  sdb: sdb1
[    7.217793] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.217798] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.876642] udev: starting version 147
[    8.807228] lp: driver loaded but no devices found
[    8.879106] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    9.037555] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[    9.037579] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[    9.572258] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[    9.627792] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    9.731765] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.038835] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[   11.038843]   alloc irq_desc for 19 on node -1
[   11.038846]   alloc kstat_irqs on node -1
[   11.038859] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 19 (level, high) -> IRQ 19
[   11.038904] HDA Intel 0000:00:10.1: setting latency timer to 64
[   12.234264] type=1505 audit(1265306222.512:12): operation="profile_replace" pid=928 name=/usr/share/gdm/guest-session/Xsession
[   12.236492] type=1505 audit(1265306222.516:13): operation="profile_replace" pid=929 name=/sbin/dhclient3
[   12.236849] type=1505 audit(1265306222.516:14): operation="profile_replace" pid=929 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.237086] type=1505 audit(1265306222.516:15): operation="profile_replace" pid=929 name=/usr/lib/connman/scripts/dhclient-script
[   12.242504] type=1505 audit(1265306222.520:16): operation="profile_replace" pid=930 name=/usr/bin/evince
[   12.248357] type=1505 audit(1265306222.528:17): operation="profile_replace" pid=930 name=/usr/bin/evince-previewer
[   12.251838] type=1505 audit(1265306222.528:18): operation="profile_replace" pid=930 name=/usr/bin/evince-thumbnailer
[   12.258889] type=1505 audit(1265306222.536:19): operation="profile_replace" pid=932 name=/usr/lib/cups/backend/cups-pdf
[   12.259325] type=1505 audit(1265306222.536:20): operation="profile_replace" pid=932 name=/usr/sbin/cupsd
[   12.261860] type=1505 audit(1265306222.540:21): operation="profile_replace" pid=933 name=/usr/sbin/tcpdump
[   14.891343] ppdev: user-space parallel port driver
[   22.727562] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   22.730344] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   22.730352]  sdb: sdb1
[   23.724039] eth0: no IPv6 routers present
[   24.728565] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   24.733344] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   24.733351]  sdb: sdb1
[   78.500067] Clocksource tsc unstable (delta = -266825873 ns)
[ 6894.476059] usb 2-1: new full speed USB device using ohci_hcd and address 3
[ 6894.700702] usb 2-1: configuration #1 chosen from 1 choice
[ 6894.765626] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7804
[ 6894.765674] usbcore: registered new interface driver usblp
[ 6895.801709] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 7305.736327] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 7305.736338] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[ 8514.724650] usblp0: removed
[ 9551.769101] sr 2:0:0:0: [sr0] Unhandled sense code
[ 9551.769112] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9551.769123] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 9551.769136] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[ 9551.769147] end_request: I/O error, dev sr0, sector 7379584
[ 9551.769161] Buffer I/O error on device sr0, logical block 922448
[ 9565.258727] sr 2:0:0:0: [sr0] Unhandled sense code
[ 9565.258738] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9565.258749] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 9565.258761] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[ 9565.258772] end_request: I/O error, dev sr0, sector 7379464
[ 9565.258785] Buffer I/O error on device sr0, logical block 922433
[ 9565.258796] Buffer I/O error on device sr0, logical block 922434
[ 9565.258804] Buffer I/O error on device sr0, logical block 922435
[ 9565.258811] Buffer I/O error on device sr0, logical block 922436
[ 9576.094955] UDF-fs: Partition marked readonly; forcing readonly mount
[ 9576.158044] UDF-fs INFO UDF: Mounting volume 'DATA070105', timestamp 2007/01/05 15:39 (1e20)
[ 9624.809506] sr 2:0:0:0: [sr0] Unhandled sense code
[ 9624.809517] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9624.809528] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 9624.809540] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[ 9624.809551] end_request: I/O error, dev sr0, sector 11656
[ 9624.809565] Buffer I/O error on device sr0, logical block 2914
[ 9658.943900] sr 2:0:0:0: [sr0] Unhandled sense code
[ 9658.943911] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9658.943922] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 9658.943934] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[ 9658.943946] end_request: I/O error, dev sr0, sector 6068
[ 9658.944061] udf: udf_read_inode(ino 1517) failed !bh
[ 9724.860101] usb 1-6: USB disconnect, address 3
[28177.941023] CE: hpet increasing min_delta_ns to 15000 nsec
```

[B]
6) Network configuration:[/B] sudo lshw -C network
returns 3 strings: 
DMI
CPUID
PCI (sysfs)
which overlay one another before shell prompt redisplays.
That's it

However if execute a vanilla lshw, I get
```
peter@peter-laptop:~$ lshw
WARNING: you should run this program as super-user.
peter-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 1949MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          size: 1700MHz
          capacity: 1700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:4000(size=4096) memory:b4000000-b7ffffff ioport:d0000000(size=2097152)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:5000(size=4096) memory:b8000000-bbffffff ioport:d0200000(size=2097152)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C51 [GeForce Go 6100]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
          resources: memory:b2000000-b2ffffff memory:c0000000-cfffffff(prefetchable) memory:b1000000-b1ffffff memory:80000000-8001ffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1d00(size=128)
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:b0040000-b007ffff
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:b0004000-b0004fff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:b0005000-b00050ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:3080(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30c0(size=8) ioport:30b4(size=4) ioport:30b8(size=8) ioport:30b0(size=4) ioport:3090(size=16) memory:b0006000-b0006fff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:19 memory:b0000000-b0003fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:36:ee:7f:8a
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.108 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:20 memory:b0008000-b0008fff ioport:30e0(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
peter@peter-laptop:~$
``` 

**7) Scan for networks** 
```
peter@peter-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning.
```
**8 ) Ubuntu Version: 9.10**(have also tried and failed under 8.10 and 9.04 which did work at one time)
**9 ) Kernel/architecture (including 32 vs. 64 bit):** 
2.6.31-17-generic i686
**10 ) Restarting the network:**
```
peter@peter-laptop:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0. 
                                                                                                                                                      [ OK ]
```

Where do I go from here?  Assistance appreciated.

---

### Post by Peter108 on 2010-02-07
Having, after some research, pretty much concluded that the on-board wireless is dead, my only (noob-ish)question is this: Is working around the problem as simple as going out and buying a USB wireless dongle (after checking the compatibility list elsewhere on this forum)?  Thanks.

---

### Post by Peter108 on 2010-02-07
I was about to order a new wireless card (20 bucks or so) when I happened across a thread in which a respondent suggested to the OP that he
[LIST=1]
[*]Unplug the unit and remove the battery
[*]Press and hold the power button for 10 seconds
[*]Re-install the battery, plug in the unit and power up
[/LIST]

As absurd as that advice appeared to my untrained eye, I nevertheless thought WTF,Why Not?  Lo and behold, I have wireless again.

---

