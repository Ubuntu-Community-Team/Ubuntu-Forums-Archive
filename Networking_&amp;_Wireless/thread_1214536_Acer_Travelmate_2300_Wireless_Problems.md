---
title: "Acer Travelmate 2300 Wireless Problems"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by rwalker83 on 2009-07-16
Hello all,

I am been trying a failing to fix this for awhile please help.

Ndis is installed
I even sudo installed the driver
I have been reading the forums and have no idea what to do.
Everytime I try and open Wireless Network Drives it comes up with an error that says: " Unable to see if hardware is present"
Ubuntu 9.04

  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:67:5b:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.10.192 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:78:d0:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.53+INPROCOMM,11/04/2004,3.03.1 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:2d:98:2e:17:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Stoneface on 2009-07-16
Maybe you could post some more data by entering the following commands from the Shell (Applications->Accessories>Terminal) :
```
uname -a
```
kernel data
```
iwconfig
```
for wireless configuration
```
sudo lspci -v
```
for listing pci busses
```
lsmod
```
to see what modules are running
```
dmesg
```
list all error messages

and posting the outcome. Like this forum members can get a better idea of what is going on and what hardware you are running. I have an Acer Aspire 4520G and had problems before which I managed to solve so so should you...

---

### Post by rwalker83 on 2009-07-16
> **Stoneface said:**
> Maybe you could post some more data by entering the following commands from the Shell (Applications->Accessories>Terminal) :
```
uname -a
```kernel data

Linux zenas-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

```
iwconfig
```for wireless configuration

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
sudo lspci -v
```for listing pci busses

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0
    Memory at <unassigned> (32-bit, prefetchable)
    Capabilities: [40] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0, IRQ 6
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Capabilities: [d0] Power Management version 1
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 1

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 10
    Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=0080
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: e0200000-e05fffff
    Prefetchable memory behind bridge: 20000000-25ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 6
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Memory at 26000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1880 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 0, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
    Memory at e0100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd-intel8x0m

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, fast devsel, latency 64, IRQ 6
    Memory at e0200000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 24000000 [disabled] [size=16K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b44
    Kernel modules: b44

02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0305
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at 3800 [size=32]
    Memory at e0203800 (32-bit, non-prefetchable) [size=32]
    Memory at e0203000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: ndiswrapper

02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 28000000-2bfff000
    I/O window 0: 00003000-000030ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

```
lsmod
```to see what modules are running

Module                  Size  Used by
b44                    35472  0 
ssb                    53128  1 b44
ndiswrapper           193436  0 
binfmt_misc            16776  1 
i915                   65668  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12036  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
video                  25360  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcspkr                 10496  0 
psmouse                61972  0 
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
serio_raw              13316  0 
shpchp                 40212  0 
pcmcia                 44748  1 ssb
pcmcia_core            43540  4 ssb,yenta_socket,rsrc_nonstatic,pcmcia
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
dmesg
```list all error messages

[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000dee0000 (usable)
[    0.000000]  BIOS-e820: 000000000dee0000 - 000000000deec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000deec000 - 000000000df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000df00000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xdee0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000dee0000 (usable)
[    0.000000]  modified: 000000000dee0000 - 000000000deec000 (ACPI data)
[    0.000000]  modified: 000000000deec000 - 000000000df00000 (ACPI NVS)
[    0.000000]  modified: 000000000df00000 - 0000000010000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to dee0000 @ 10000-16000
[    0.000000] RAMDISK: 0d799000 - 0decfac1
[    0.000000] ACPI: RSDP 000F62E0, 0014 (r0 ACER  )
[    0.000000] ACPI: RSDT 0DEE7C68, 0030 (r1 ACER   Kestrel  20020803  LTP        0)
[    0.000000] ACPI: FACP 0DEEBF2C, 0074 (r1 ACER   Kestrel  20020803 PTL        50)
[    0.000000] ACPI: DSDT 0DEE7C98, 4294 (r1 ACER   Kestrel  20020803 MSFT  100000E)
[    0.000000] ACPI: FACS 0DEFCFC0, 0040
[    0.000000] ACPI: HPET 0DEEBFA0, 0038 (r1 ACER   Kestrel  20020803 PTL         0)
[    0.000000] ACPI: BOOT 0DEEBFD8, 0028 (r1 ACER   Kestrel  20020803  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 222MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0dee0000
[    0.000000]   low ram: 00000000 - 0dee0000
[    0.000000]   bootmap 00012000 - 00013bdc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000dee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [000d799000 - 000decfac1]          RAMDISK ==> [000d799000 - 000decfac1]
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000dee0
[    0.000000]   HighMem  0x0000dee0 -> 0x0000dee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000dee0
[    0.000000] On node 0 totalpages: 56933
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 414 pages used for memmap
[    0.000000]   Normal zone: 52546 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec10000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56487
[    0.000000] Kernel command line: root=UUID=ad77ccb9-76a8-4176-bfd2-ae87f04a2d9a ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1498.679 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1141120 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 209280k/228224k available (4110k kernel code, 18252k reserved, 2196k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xce6e0000 - 0xff3fe000   ( 781 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcdee0000   ( 222 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 2997.35 BogoMIPS (lpj=5994716)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016848] SMP alternatives: switching to UP code
[    0.144679] Freeing SMP alternatives: 18k freed
[    0.144687] ACPI: Core revision 20080926
[    0.147086] ACPI: Checking initramfs for custom DSDT
[    0.544729] ACPI: setting ELCR to 0200 (from 0440)
[    0.548076] weird, boot CPU (#0) not listedby the BIOS.
[    0.548079] SMP motherboard not detected.
[    0.548082] Local APIC not detected. Using dummy APIC emulation.
[    0.548085] SMP disabled
[    0.548396] Brought up 1 CPUs
[    0.548399] Total of 1 processors activated (2997.35 BogoMIPS).
[    0.548415] CPU0 attaching NULL sched-domain.
[    0.548787] net_namespace: 776 bytes
[    0.548799] Booting paravirtualized kernel on bare hardware
[    0.549145] Time: 23:03:41  Date: 07/14/09
[    0.549153] regulator: core version 0.5
[    0.549204] NET: Registered protocol family 16
[    0.549373] EISA bus registered
[    0.549395] ACPI: bus type pci registered
[    0.552270] PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
[    0.552273] PCI: Using configuration type 1 for base access
[    0.554259] ACPI: EC: Look up EC in DSDT
[    0.558215] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.560602] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.589340] ACPI: Interpreter enabled
[    0.589345] ACPI: (supports S0 S3 S4 S5)
[    0.589364] ACPI: Using PIC for interrupt routing
[    0.593452] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.593456] ACPI: EC: driver started in interrupt mode
[    0.593593] ACPI: No dock devices found.
[    0.593605] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.593750] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.593755] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.593761] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.593778] pci 0000:00:02.0: supports D1
[    0.593795] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.593801] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.593819] pci 0000:00:02.1: supports D1
[    0.593885] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.593932] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.593978] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.594032] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.594072] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.594077] pci 0000:00:1d.7: PME# disabled
[    0.594150] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.594157] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.594162] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.594181] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.594188] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.594195] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.594201] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.594208] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.594216] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.594260] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.594297] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.594303] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.594310] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.594317] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.594337] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.594342] pci 0000:00:1f.5: PME# disabled
[    0.594369] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.594376] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.594403] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.594408] pci 0000:00:1f.6: PME# disabled
[    0.594442] pci 0000:02:02.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    0.594468] pci 0000:02:02.0: reg 30 32bit mmio: [0x000000-0x003fff]
[    0.594477] pci 0000:02:02.0: supports D1 D2
[    0.594479] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594484] pci 0000:02:02.0: PME# disabled
[    0.594511] pci 0000:02:04.0: reg 10 io port: [0x3800-0x381f]
[    0.594518] pci 0000:02:04.0: reg 14 32bit mmio: [0xe0203800-0xe020381f]
[    0.594526] pci 0000:02:04.0: reg 18 32bit mmio: [0xe0203000-0xe02037ff]
[    0.594550] pci 0000:02:04.0: supports D2
[    0.594580] pci 0000:02:06.0: reg 10 32bit mmio: [0xe0202000-0xe0202fff]
[    0.594589] pci 0000:02:06.0: supports D1 D2
[    0.594592] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.594596] pci 0000:02:06.0: PME# disabled
[    0.594634] pci 0000:00:1e.0: transparent bridge
[    0.594639] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.594644] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe05fffff]
[    0.594668] bus 00 -> node 0
[    0.594676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.594998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.597610] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    0.597745] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.597879] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.598010] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    0.598143] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.598275] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.598408] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    0.598542] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.598656] ACPI: Power Resource [PFN0] (off)
[    0.598712] ACPI: Power Resource [PFN1] (off)
[    0.598813] ACPI: WMI: Mapper loaded
[    0.599069] SCSI subsystem initialized
[    0.599123] libata version 3.00 loaded.
[    0.599182] usbcore: registered new interface driver usbfs
[    0.599206] usbcore: registered new interface driver hub
[    0.599242] usbcore: registered new device driver usb
[    0.599381] PCI: Using ACPI for IRQ routing
[    0.599501] Bluetooth: Core ver 2.13
[    0.599501] NET: Registered protocol family 31
[    0.599501] Bluetooth: HCI device and connection manager initialized
[    0.599501] Bluetooth: HCI socket layer initialized
[    0.599501] NET: Registered protocol family 8
[    0.599501] NET: Registered protocol family 20
[    0.599501] NetLabel: Initializing
[    0.599501] NetLabel:  domain hash size = 128
[    0.599501] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.599501] NetLabel:  unlabeled traffic allowed by default
[    0.599501] AppArmor: AppArmor Filesystem Enabled
[    0.599501] pnp: PnP ACPI init
[    0.599501] ACPI: bus type pnp registered
[    0.602049] pnp: PnP ACPI: found 8 devices
[    0.602052] ACPI: ACPI bus type pnp unregistered
[    0.602057] PnPBIOS: Disabled by ACPI PNP
[    0.602071] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.602077] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.602080] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.602084] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.602087] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.602091] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.602094] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    0.602099] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.602102] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.602106] system 00:04: ioport range 0x610-0x61f has been reserved
[    0.602116] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.602120] system 00:04: iomem range 0xff800000-0xffbfffff has been reserved
[    0.602124] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.602128] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    0.602131] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    0.602135] system 00:04: iomem range 0xdf800-0xdffff could not be reserved
[    0.636885] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.636889] pci 0000:02:06.0:   IO window: 0x003000-0x0030ff
[    0.636894] pci 0000:02:06.0:   IO window: 0x003400-0x0034ff
[    0.636899] pci 0000:02:06.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.636904] pci 0000:02:06.0:   MEM window: 0x28000000-0x2bffffff
[    0.636908] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.636912] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.636918] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe05fffff
[    0.636923] pci 0000:00:1e.0:   PREFETCH window: 0x00000020000000-0x00000025ffffff
[    0.636939] pci 0000:00:1e.0: setting latency timer to 64
[    0.636948] pci 0000:02:06.0: enabling device (0104 -> 0107)
[    0.637164] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    0.637168] PCI: setting IRQ 10 as level-triggered
[    0.637173] pci 0000:02:06.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    0.637180] bus: 00 index 0 io port: [0x00-0xffff]
[    0.637184] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.637187] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.637190] bus: 02 index 1 mmio: [0xe0200000-0xe05fffff]
[    0.637192] bus: 02 index 2 mmio: [0x20000000-0x25ffffff]
[    0.637195] bus: 02 index 3 io port: [0x00-0xffff]
[    0.637198] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.637201] bus: 03 index 0 io port: [0x3000-0x30ff]
[    0.637203] bus: 03 index 1 io port: [0x3400-0x34ff]
[    0.637206] bus: 03 index 2 mmio: [0x20000000-0x23ffffff]
[    0.637209] bus: 03 index 3 mmio: [0x28000000-0x2bffffff]
[    0.637227] NET: Registered protocol family 2
[    0.637388] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.637716] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.637784] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.637846] TCP: Hash tables configured (established 8192 bind 8192)
[    0.637849] TCP reno registered
[    0.637953] NET: Registered protocol family 1
[    0.638114] checking if image is initramfs... it is
[    1.140071] Switched to high resolution mode on CPU 0
[    1.458374] Freeing initrd memory: 7386k freed
[    1.458434] Simple Boot Flag at 0x37 set to 0x1
[    1.458467] cpufreq: No nForce2 chipset.
[    1.458649] audit: initializing netlink socket (disabled)
[    1.458676] type=2000 audit(1247612621.456:1): initialized
[    1.468670] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.470562] VFS: Disk quotas dquot_6.5.1
[    1.470649] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.471561] fuse init (API version 7.10)
[    1.471684] msgmni has been set to 423
[    1.471941] alg: No test for stdrng (krng)
[    1.471958] io scheduler noop registered
[    1.471961] io scheduler anticipatory registered
[    1.471963] io scheduler deadline registered
[    1.471994] io scheduler cfq registered (default)
[    1.472051] pci 0000:00:02.0: Boot video device
[    1.474167] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.474179] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.474351] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.474355] ACPI: Power Button (FF) [PWRF]
[    1.474421] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.477142] ACPI: Lid Switch [LID]
[    1.477207] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.477211] ACPI: Sleep Button (CM) [SLPB]
[    1.477393] fan PNP0C0B:00: registered as cooling_device0
[    1.477400] ACPI: Fan [FAN0] (off)
[    1.477543] fan PNP0C0B:01: registered as cooling_device1
[    1.477550] ACPI: Fan [FAN1] (off)
[    1.477708] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.477729] processor ACPI_CPU:00: registered as cooling_device2
[    1.477734] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.482135] thermal LNXTHERM:01: registered as thermal_zone0
[    1.487817] ACPI: Thermal Zone [THRM] (44 C)
[    1.487850] ACPI: SBS HC: EC = 0xcd00ce40, offset = 0x18, query_bit = 0x20
[    1.501857] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[    1.855525] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[    1.855547] isapnp: Scanning for PnP cards...
[    2.209132] isapnp: No Plug & Play device found
[    2.286912] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.287583] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    2.287590] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.287599] serial 0000:00:1f.6: PCI INT B disabled
[    2.288467] brd: module loaded
[    2.288875] loop: module loaded
[    2.288991] Fixed MDIO Bus: probed
[    2.288999] PPP generic driver version 2.4.2
[    2.289080] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.289125] Driver 'sd' needs updating - please use bus_type methods
[    2.289136] Driver 'sr' needs updating - please use bus_type methods
[    2.289231] ata_piix 0000:00:1f.1: version 2.12
[    2.289249] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    2.289255] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.289492] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    2.289497] PCI: setting IRQ 6 as level-triggered
[    2.289502] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    2.289552] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.289684] scsi0 : ata_piix
[    2.289834] scsi1 : ata_piix
[    2.291155] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.291159] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.452547] ata1.00: ATA-6: HTS541040G9AT00, MB2OA60A, max UDMA/100
[    2.452550] ata1.00: 78140160 sectors, multi 16: LBA48 
[    2.468508] ata1.00: configured for UDMA/100
[    2.632285] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[    2.648254] ata2.00: configured for UDMA/33
[    2.648599] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2O PQ: 0 ANSI: 5
[    2.648732] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.648753] sd 0:0:0:0: [sda] Write Protect is off
[    2.648756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.648786] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.648875] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.648893] sd 0:0:0:0: [sda] Write Protect is off
[    2.648896] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.648923] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.648928]  sda: sda1 sda2 < sda5 >
[    2.709050] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.709120] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.709680] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    2.712385] sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    2.712390] Uniform CD-ROM driver Revision: 3.20
[    2.712526] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.712583] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.713393] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.713676] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    2.713682] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    2.713716] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.713721] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.713817] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.717739] ehci_hcd 0000:00:1d.7: debug port 1
[    2.717746] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.717758] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    2.732028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.732136] usb usb1: configuration #1 chosen from 1 choice
[    2.732172] hub 1-0:1.0: USB hub found
[    2.732183] hub 1-0:1.0: 6 ports detected
[    2.732328] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.732356] uhci_hcd: USB Universal Host Controller Interface driver
[    2.732641] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    2.732646] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[    2.732656] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.732660] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.732727] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.732752] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    2.732852] usb usb2: configuration #1 chosen from 1 choice
[    2.732884] hub 2-0:1.0: USB hub found
[    2.732897] hub 2-0:1.0: 2 ports detected
[    2.733231] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    2.733236] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    2.733243] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.733247] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.733308] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.733328] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    2.733424] usb usb3: configuration #1 chosen from 1 choice
[    2.733461] hub 3-0:1.0: USB hub found
[    2.733469] hub 3-0:1.0: 2 ports detected
[    2.733566] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 6 (level, low) -> IRQ 6
[    2.733573] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.733576] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.733627] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.733647] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    2.733744] usb usb4: configuration #1 chosen from 1 choice
[    2.733775] hub 4-0:1.0: USB hub found
[    2.733788] hub 4-0:1.0: 2 ports detected
[    2.733958] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[    2.735940] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.736918] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.736926] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.736929] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.736932] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.736935] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.737136] mice: PS/2 mouse device common for all mice
[    2.737371] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.737390] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.737501] device-mapper: uevent: version 1.0.3
[    2.737665] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.737729] device-mapper: multipath: version 1.0.5 loaded
[    2.737732] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.737861] EISA: Probing bus 0 at eisa.0
[    2.737869] Cannot allocate resource for EISA slot 1
[    2.737873] Cannot allocate resource for EISA slot 2
[    2.737876] Cannot allocate resource for EISA slot 3
[    2.737898] EISA: Detected 0 cards.
[    2.737978] cpuidle: using governor ladder
[    2.738054] cpuidle: using governor menu
[    2.738812] TCP cubic registered
[    2.738964] NET: Registered protocol family 10
[    2.739542] lo: Disabled Privacy Extensions
[    2.739998] NET: Registered protocol family 17
[    2.740056] Bluetooth: L2CAP ver 2.11
[    2.740058] Bluetooth: L2CAP socket layer initialized
[    2.740062] Bluetooth: SCO (Voice Link) ver 0.6
[    2.740064] Bluetooth: SCO socket layer initialized
[    2.740104] Bluetooth: RFCOMM socket layer initialized
[    2.740114] Bluetooth: RFCOMM TTY layer initialized
[    2.740116] Bluetooth: RFCOMM ver 1.10
[    2.740190] ACPI Exception (processor_perflib-0270): AE_NOT_FOUND, Evaluating _PSS [20080926]
[    2.740204] IO APIC resources could be not be allocated.
[    2.740250] Using IPI No-Shortcut mode
[    2.740383] registered taskstats version 1
[    2.740536]   Magic number: 1:13:100
[    2.740652] rtc_cmos 00:01: setting system clock to 2009-07-14 23:03:43 UTC (1247612623)
[    2.740656] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.740659] EDD information not available.
[    2.741054] Freeing unused kernel memory: 532k freed
[    2.741249] Write protecting the kernel text: 4112k
[    2.741299] Write protecting the kernel read-only data: 1524k
[    2.782330] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.836273] hub 2-0:1.0: over-current change on port 1
[    2.948046] hub 2-0:1.0: over-current change on port 2
[    3.443372] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.500170] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    3.500202] b44.c:v2.0
[    3.521009] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet cbb38948
[    3.856874] Marking TSC unstable due to TSC halts in idle
[    3.908823] PM: Starting manual resume from disk
[    3.908828] PM: Resume from partition 8:5
[    3.908831] PM: Checking hibernation image.
[    3.909065] PM: Resume from disk failed.
[    3.957911] kjournald starting.  Commit interval 5 seconds
[    3.957929] EXT3-fs: mounted filesystem with ordered data mode.
[   11.213495] udev: starting version 141
[   11.524836] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.569504] intel_rng: FWH not detected
[   11.593922] Linux agpgart interface v0.103
[   11.699258] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   11.699489] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[   11.701061] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   11.766058] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.906622] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.922043] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.090641] yenta_cardbus 0000:02:06.0: CardBus bridge found [1025:0064]
[   12.090659] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   12.090664] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   12.090668] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   12.090673] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01a21b22, devctl 0x64
[   12.109922] acpi device:06: registered as cooling_device3
[   12.110154] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/input/input6
[   12.117978] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   12.246852] iTCO_vendor_support: vendor-support=0
[   12.250138] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.250289] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   12.250397] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.258072] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.258092] acer-wmi: No or unsupported WMI interface, unable to load
[   12.326955] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x08b8, PCI irq 10
[   12.326961] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   12.326966] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   12.326977] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   12.326983] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   12.327261] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   12.327265] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   12.587983] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   12.588188] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.636033] Clocksource tsc unstable (delta = -106565594 ns)
[   12.647559] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.649188] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   12.649884] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.650463] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.651220] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.908836] intel8x0_measure_ac97_clock: measured 54578 usecs
[   12.908841] intel8x0: clocking to 48000
[   12.923317] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   12.970443] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   13.107452] ndiswrapper: driver neti2220 (INPROCOMM,11/04/2004,3.03.11.2004) loaded
[   13.107759] ndiswrapper 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.141867] ndiswrapper: using IRQ 10
[   13.341531] wlan0: ethernet device 00:0e:9b:78:d0:4c using NDIS driver: neti2220, version: 0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
[   13.341558] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.342856] usbcore: registered new interface driver ndiswrapper
[   13.555447] lp: driver loaded but no devices found
[   13.648353] Adding 634528k swap on /dev/sda5.  Priority:-1 extents:1 across:634528k
[   14.198418] EXT3 FS on sda1, internal journal
[   15.366922] type=1505 audit(1247612636.123:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1921
[   15.439304] type=1505 audit(1247612636.195:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1925
[   15.439567] type=1505 audit(1247612636.195:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1925
[   15.439665] type=1505 audit(1247612636.195:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1925
[   15.439739] type=1505 audit(1247612636.195:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1925
[   15.652126] type=1505 audit(1247612636.411:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1930
[   15.652527] type=1505 audit(1247612636.411:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1930
[   15.695298] type=1505 audit(1247612636.451:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1934
[   18.114851] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.114855] Bluetooth: BNEP filters: protocol multicast
[   18.143256] Bridge firewalling registered
[   20.108054] ppdev: user-space parallel port driver
[   20.803982] [drm] Initialized drm 1.1.0 20060810
[   20.853554] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 6 (level, low) -> IRQ 6
[   20.853562] pci 0000:00:02.0: setting latency timer to 64
[   20.853796] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   20.858295] [drm:i915_setparam] *ERROR* unknown parameter 4
[   20.858328] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   21.973326] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   23.244893] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.816190] b44: eth0: Link is up at 100 Mbps, full duplex.
[   26.816195] b44: eth0: Flow control is off for TX and off for RX.
[   26.816294] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.544237] wlan0: no IPv6 routers present
[   37.272046] eth0: no IPv6 routers present
[   40.912058] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  682.568035] hub 2-0:1.0: over-current change on port 2
[  720.852036] hub 2-0:1.0: over-current change on port 2
[  729.460039] hub 2-0:1.0: over-current change on port 2
[ 1242.664203] ndiswrapper: device wlan0 removed
[ 1242.664236] ndiswrapper 0000:02:04.0: PCI INT A disabled
[ 1242.664323] usbcore: deregistering interface driver ndiswrapper
[ 1277.106944] b44: eth0: powering down PHY
[ 1277.396387] b44 0000:02:02.0: PCI INT A disabled
[ 1317.887081] ndiswrapper: Unknown parameter `wrapper'
[ 1341.024576] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1341.167695] ndiswrapper: driver neti2220 (INPROCOMM,11/04/2004,3.03.11.2004) loaded
[ 1341.168056] ndiswrapper 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[ 1341.202734] ndiswrapper: using IRQ 10
[ 1341.404396] wlan0: ethernet device 00:0e:9b:78:d0:4c using NDIS driver: neti2220, version: 0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
[ 1341.404425] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1341.404521] usbcore: registered new interface driver ndiswrapper
[ 1352.808071] b44 0000:02:02.0: PCI INT A -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[ 1352.868321] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[ 1352.868353] b44.c:v2.0
[ 1352.889173] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet ccad1948
[ 1356.836241] wlan0: no IPv6 routers present
[ 1357.244349] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1360.000399] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1360.000404] b44: eth0: Flow control is off for TX and off for RX.
[ 1360.000519] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1370.112240] eth0: no IPv6 routers present
[ 1433.200926] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1433.200932] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1433.200935] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 2177.399658] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4001.000314] b44: eth0: Link is down.
[16372.003747] [drm:i915_getparam] *ERROR* Unknown parameter 6

and posting the outcome. Like this forum members can get a better idea of what is going on and what hardware you are running. I have an Acer Aspire 4520G and had problems before which I managed to solve so so should you...

All help is greatly appreciated.

---

### Post by rwalker83 on 2009-07-16
bump

---

