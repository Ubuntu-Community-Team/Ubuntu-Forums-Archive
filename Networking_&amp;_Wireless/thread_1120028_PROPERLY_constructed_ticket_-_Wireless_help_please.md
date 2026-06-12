---
title: "PROPERLY constructed ticket - Wireless help please"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by dax702 on 2009-04-08
I should first start by saying that I'm a complete noob to anything Linux (but plenty of experience with M$). I downloaded, burned and installed 9.04 Beta on my Gateway 4026GZ laptop.

Prior to installing it, I ran the first option of trying Ubuntu without installing it and the wireless worked fine.

After taking the plunge and actually installing Ubuntu, I have nothing happening in terms of wireless internet. It's a Broadcom BCM4306 rev 03

**[COLOR="Blue"]Here is the info from the instructions on creating a proper ticket:[/COLOR]**

[B]angie@angie-laptop:~$ lspci -nn | grep 'Wireless Brand'
angie@angie-laptop:~$ lspci[/B]
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
angie@angie-laptop:~$ 
**angie@angie-laptop:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**angie@angie-laptop:~$ iwconfig wlan0**
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**angie@angie-laptop:~$ lsmod | grep "wlan_module_name"**
**angie@angie-laptop:~$ lsmod**
Module                  Size  Used by
rfkill_input           12800  0 
binfmt_misc            16776  1 
i915                   65668  2 
drm                    96424  3 i915
ppdev                  15492  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
arc4                    9856  2 
snd_pcm                82820  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
b43                   131612  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217080  1 b43
pcmcia                 44748  0 
cfg80211               38032  1 mac80211
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 b43
intel_agp              34108  1 
soundcore              15200  1 snd
input_polldev          11912  1 b43
psmouse                61972  0 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
serio_raw              13316  0 
video                  25360  0 
shpchp                 40212  0 
output                 11008  1 video
usbhid                 42336  0 
ohci1394               38576  0 
ssb                    41220  1 b43
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
**angie@angie-laptop:~$ dmesg**
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009 (Ubuntu 2.6.28-11.37-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004dee0000 (usable)
[    0.000000]  BIOS-e820: 000000004dee0000 - 000000004deeb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004deeb000 - 000000004df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004df00000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x4dee0 max_arch_pfn = 0x100000
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
[    0.000000]  modified: 0000000000100000 - 000000004dee0000 (usable)
[    0.000000]  modified: 000000004dee0000 - 000000004deeb000 (ACPI data)
[    0.000000]  modified: 000000004deeb000 - 000000004df00000 (ACPI NVS)
[    0.000000]  modified: 000000004df00000 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c1000 - 37fef1b4
[    0.000000] Allocated new RAMDISK: 00881000 - 00faf1b4
[    0.000000] Move RAMDISK from 00000000378c1000 - 0000000037fef1b3 to 00881000 - 00faf1b3
[    0.000000] ACPI: RSDP 000F7780, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 4DEE69CD, 0030 (r1 PTLTD  ManiaDth  6040000  LTP        0)
[    0.000000] ACPI: FACP 4DEEAEC4, 0074 (r1 INTEL  MONTARA   6040000 PTL        50)
[    0.000000] ACPI: DSDT 4DEE6F0E, 3FB6 (r1 INTEL  MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 4DEFBFC0, 0040
[    0.000000] ACPI: BOOT 4DEEAFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 4DEE6DFD, 0109 (r1 INTEL  CPU0CST         1 INTL 20030224)
[    0.000000] 362MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000faf1b4]      NEW RAMDISK ==> [0000881000 - 0000faf1b4]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0004dee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0004dee0
[    0.000000] On node 0 totalpages: 319077
[    0.000000] free_area_init_node: node 0, pgdat c06d0f00, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 726 pages used for memmap
[    0.000000]   HighMem zone: 92172 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:af800000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 316583
[    0.000000] Kernel command line: root=UUID=578186f3-b490-4676-9279-ebd28a9d1b3d ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1295.801 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 6384000 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1243248k/1276800k available (4126k kernel code, 32160k reserved, 2208k data, 532k init, 371592k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a7f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a7f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 2591.60 BogoMIPS (lpj=5183204)
[    0.004054] Security Framework initialized
[    0.004072] SELinux:  Disabled at boot.
[    0.004108] AppArmor: AppArmor initialized
[    0.004122] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys ns
[    0.004363] Initializing cgroup subsys cpuacct
[    0.004367] Initializing cgroup subsys memory
[    0.004373] Initializing cgroup subsys freezer
[    0.004398] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004402] CPU: L2 cache: 1024K
[    0.004425] Checking 'hlt' instruction... OK.
[    0.020974] SMP alternatives: switching to UP code
[    0.172680] Freeing SMP alternatives: 18k freed
[    0.172686] ACPI: Core revision 20080926
[    0.175028] ACPI: Checking initramfs for custom DSDT
[    0.627705] ACPI: setting ELCR to 0200 (from 0c28)
[    0.628076] weird, boot CPU (#0) not listedby the BIOS.
[    0.628079] SMP motherboard not detected.
[    0.628083] Local APIC not detected. Using dummy APIC emulation.
[    0.628086] SMP disabled
[    0.628399] Brought up 1 CPUs
[    0.628402] Total of 1 processors activated (2591.60 BogoMIPS).
[    0.628418] CPU0 attaching NULL sched-domain.
[    0.628788] net_namespace: 776 bytes
[    0.628801] Booting paravirtualized kernel on bare hardware
[    0.629093] Time:  7:51:11  Date: 04/07/09
[    0.629101] regulator: core version 0.5
[    0.629146] NET: Registered protocol family 16
[    0.629319] EISA bus registered
[    0.629340] ACPI: bus type pci registered
[    0.632312] PCI: PCI BIOS revision 2.10 entry at 0xfd932, last bus=2
[    0.632315] PCI: Using configuration type 1 for base access
[    0.634308] ACPI: EC: Look up EC in DSDT
[    0.637210] ACPI: Interpreter enabled
[    0.637216] ACPI: (supports S0 S3 S4 S5)
[    0.637240] ACPI: Using PIC for interrupt routing
[    0.637667] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.641467] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.641471] ACPI: EC: driver started in interrupt mode
[    0.641611] ACPI: No dock devices found.
[    0.641628] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.641779] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.641786] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.641792] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.641810] pci 0000:00:02.0: supports D1
[    0.641829] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.641836] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.641855] pci 0000:00:02.1: supports D1
[    0.641926] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.641977] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.642026] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.642083] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.642125] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.642131] pci 0000:00:1d.7: PME# disabled
[    0.642209] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.642216] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.642221] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.642242] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.642249] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.642257] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.642264] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.642272] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.642280] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.642327] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.642366] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.642374] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.642381] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.642389] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.642411] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.642416] pci 0000:00:1f.5: PME# disabled
[    0.642445] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.642453] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.642482] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.642487] pci 0000:00:1f.6: PME# disabled
[    0.642530] pci 0000:02:07.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.642540] pci 0000:02:07.0: supports D1 D2
[    0.642543] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.642548] pci 0000:02:07.0: PME# disabled
[    0.642577] pci 0000:02:07.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.642586] pci 0000:02:07.1: supports D1 D2
[    0.642589] pci 0000:02:07.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.642594] pci 0000:02:07.1: PME# disabled
[    0.642623] pci 0000:02:07.2: reg 10 32bit mmio: [0xe0202000-0xe02027ff]
[    0.642657] pci 0000:02:07.2: PME# supported from D0 D3hot D3cold
[    0.642662] pci 0000:02:07.2: PME# disabled
[    0.642697] pci 0000:02:08.0: reg 10 io port: [0x3000-0x30ff]
[    0.642705] pci 0000:02:08.0: reg 14 32bit mmio: [0xe0202800-0xe02028ff]
[    0.642736] pci 0000:02:08.0: supports D1 D2
[    0.642739] pci 0000:02:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.642744] pci 0000:02:08.0: PME# disabled
[    0.642764] pci 0000:02:09.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    0.642818] pci 0000:00:1e.0: transparent bridge
[    0.642824] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.642829] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe02fffff]
[    0.642871] bus 00 -> node 0
[    0.642880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.643239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.646610] ACPI: PCI Interrupt Link [LNKA] (IRQs *5)
[    0.646746] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.646878] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[    0.647011] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.647143] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.647282] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.647421] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.647560] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.647712] ACPI: WMI: Mapper loaded
[    0.647949] SCSI subsystem initialized
[    0.648014] libata version 3.00 loaded.
[    0.648082] usbcore: registered new interface driver usbfs
[    0.648107] usbcore: registered new interface driver hub
[    0.648142] usbcore: registered new device driver usb
[    0.648293] PCI: Using ACPI for IRQ routing
[    0.648411] Bluetooth: Core ver 2.13
[    0.648411] NET: Registered protocol family 31
[    0.648411] Bluetooth: HCI device and connection manager initialized
[    0.648411] Bluetooth: HCI socket layer initialized
[    0.648411] NET: Registered protocol family 8
[    0.648411] NET: Registered protocol family 20
[    0.648411] NetLabel: Initializing
[    0.648411] NetLabel:  domain hash size = 128
[    0.648411] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.648411] NetLabel:  unlabeled traffic allowed by default
[    0.648411] AppArmor: AppArmor Filesystem Enabled
[    0.648411] pnp: PnP ACPI init
[    0.648411] ACPI: bus type pnp registered
[    0.649935] pnp: PnP ACPI: found 8 devices
[    0.649938] ACPI: ACPI bus type pnp unregistered
[    0.649943] PnPBIOS: Disabled by ACPI PNP
[    0.649959] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.649963] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.649966] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.649970] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.649974] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.649979] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.649984] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.685848] pci 0000:02:07.0: CardBus bridge, secondary bus 0000:03
[    0.685852] pci 0000:02:07.0:   IO window: 0x003400-0x0034ff
[    0.685857] pci 0000:02:07.0:   IO window: 0x003800-0x0038ff
[    0.685862] pci 0000:02:07.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.685868] pci 0000:02:07.0:   MEM window: 0x6c000000-0x6fffffff
[    0.685873] pci 0000:02:07.1: CardBus bridge, secondary bus 0000:07
[    0.685876] pci 0000:02:07.1:   IO window: 0x003c00-0x003cff
[    0.685881] pci 0000:02:07.1:   IO window: 0x001400-0x0014ff
[    0.685886] pci 0000:02:07.1:   PREFETCH window: 0x64000000-0x67ffffff
[    0.685891] pci 0000:02:07.1:   MEM window: 0x70000000-0x73ffffff
[    0.685897] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.685901] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.685908] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    0.685913] pci 0000:00:1e.0:   PREFETCH window: 0x00000060000000-0x00000067ffffff
[    0.685930] pci 0000:00:1e.0: setting latency timer to 64
[    0.686145] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.686148] PCI: setting IRQ 11 as level-triggered
[    0.686154] pci 0000:02:07.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.686160] pci 0000:02:07.0: setting latency timer to 64
[    0.686358] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.686361] PCI: setting IRQ 10 as level-triggered
[    0.686366] pci 0000:02:07.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.686372] pci 0000:02:07.1: setting latency timer to 64
[    0.686377] bus: 00 index 0 io port: [0x00-0xffff]
[    0.686380] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.686384] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.686387] bus: 02 index 1 mmio: [0xe0200000-0xe02fffff]
[    0.686391] bus: 02 index 2 mmio: [0x60000000-0x67ffffff]
[    0.686394] bus: 02 index 3 io port: [0x00-0xffff]
[    0.686397] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.686400] bus: 03 index 0 io port: [0x3400-0x34ff]
[    0.686403] bus: 03 index 1 io port: [0x3800-0x38ff]
[    0.686406] bus: 03 index 2 mmio: [0x60000000-0x63ffffff]
[    0.686410] bus: 03 index 3 mmio: [0x6c000000-0x6fffffff]
[    0.686413] bus: 07 index 0 io port: [0x3c00-0x3cff]
[    0.686416] bus: 07 index 1 io port: [0x1400-0x14ff]
[    0.686419] bus: 07 index 2 mmio: [0x64000000-0x67ffffff]
[    0.686423] bus: 07 index 3 mmio: [0x70000000-0x73ffffff]
[    0.686436] NET: Registered protocol family 2
[    0.686592] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.686951] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.688441] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.689533] TCP: Hash tables configured (established 131072 bind 65536)
[    0.689538] TCP reno registered
[    0.689758] NET: Registered protocol family 1
[    0.689970] checking if image is initramfs... it is
[    1.188055] Switched to high resolution mode on CPU 0
[    1.621059] Freeing initrd memory: 7352k freed
[    1.621134] Simple Boot Flag at 0x36 set to 0x1
[    1.621176] cpufreq: No nForce2 chipset.
[    1.621386] audit: initializing netlink socket (disabled)
[    1.621417] type=2000 audit(1239090671.620:1): initialized
[    1.634765] highmem bounce pool size: 64 pages
[    1.634775] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.636655] VFS: Disk quotas dquot_6.5.1
[    1.636745] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.637596] fuse init (API version 7.10)
[    1.637711] msgmni has been set to 1718
[    1.637969] alg: No test for stdrng (krng)
[    1.637987] io scheduler noop registered
[    1.637990] io scheduler anticipatory registered
[    1.637992] io scheduler deadline registered
[    1.638015] io scheduler cfq registered (default)
[    1.638041] pci 0000:00:02.0: Boot video device
[    1.640728] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.640742] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.641232] ACPI: AC Adapter [AC] (on-line)
[    1.671956] ACPI: Battery Slot [BAT0] (battery present)
[    1.672066] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.672070] ACPI: Power Button (FF) [PWRF]
[    1.672131] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.672763] ACPI: Lid Switch [LID0]
[    1.672826] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.672834] ACPI: Sleep Button (CM) [SLPB]
[    1.672891] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.672896] ACPI: Power Button (CM) [PWRB]
[    1.673301] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.673335] processor ACPI_CPU:00: registered as cooling_device0
[    1.673341] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.675319] thermal LNXTHERM:01: registered as thermal_zone0
[    1.676020] ACPI: Thermal Zone [THRM] (77 C)
[    1.676077] isapnp: Scanning for PnP cards...
[    2.029774] isapnp: No Plug & Play device found
[    2.031405] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.031852] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    2.031861] serial 0000:00:1f.6: PCI INT B disabled
[    2.032804] brd: module loaded
[    2.033225] loop: module loaded
[    2.033323] Fixed MDIO Bus: probed
[    2.033332] PPP generic driver version 2.4.2
[    2.033409] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.033448] Driver 'sd' needs updating - please use bus_type methods
[    2.033461] Driver 'sr' needs updating - please use bus_type methods
[    2.033563] ata_piix 0000:00:1f.1: version 2.12
[    2.033572] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.033811] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    2.033816] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    2.033866] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.033977] scsi0 : ata_piix
[    2.034158] scsi1 : ata_piix
[    2.035574] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.035578] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.196554] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    2.196559] ata1.00: 78140160 sectors, multi 16: LBA48 
[    2.212512] ata1.00: configured for UDMA/100
[    2.376290] ata2.00: ATAPI: TSSTcorpCDW/DVD TS-L462A, AI30, max UDMA/33
[    2.408264] ata2.00: configured for UDMA/33
[    2.413063] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    2.413199] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.413223] sd 0:0:0:0: [sda] Write Protect is off
[    2.413227] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.413262] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.413341] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.413361] sd 0:0:0:0: [sda] Write Protect is off
[    2.413364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.413398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.413403]  sda: sda1 sda2 < sda5 >
[    2.461915] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.461975] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.475130] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462A AI30 PQ: 0 ANSI: 5
[    2.520171] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.520176] Uniform CD-ROM driver Revision: 3.20
[    2.520293] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.520341] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.521180] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.521439] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 3
[    2.521444] PCI: setting IRQ 3 as level-triggered
[    2.521450] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 3 (level, low) -> IRQ 3
[    2.521480] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.521485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.521575] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.525490] ehci_hcd 0000:00:1d.7: debug port 1
[    2.525498] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.525508] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xe0100000
[    2.540027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.540130] usb usb1: configuration #1 chosen from 1 choice
[    2.540168] hub 1-0:1.0: USB hub found
[    2.540179] hub 1-0:1.0: 6 ports detected
[    2.540332] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.540355] uhci_hcd: USB Universal Host Controller Interface driver
[    2.540598] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    2.540601] PCI: setting IRQ 5 as level-triggered
[    2.540606] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    2.540616] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.540620] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.540680] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.540704] uhci_hcd 0000:00:1d.0: irq 5, io base 0x00001820
[    2.540809] usb usb2: configuration #1 chosen from 1 choice
[    2.540842] hub 2-0:1.0: USB hub found
[    2.540852] hub 2-0:1.0: 2 ports detected
[    2.540958] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.540965] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.540970] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.541028] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.541049] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    2.541138] usb usb3: configuration #1 chosen from 1 choice
[    2.541172] hub 3-0:1.0: USB hub found
[    2.541189] hub 3-0:1.0: 2 ports detected
[    2.541287] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    2.541295] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.541299] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.541353] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.541375] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[    2.541464] usb usb4: configuration #1 chosen from 1 choice
[    2.541502] hub 4-0:1.0: USB hub found
[    2.541510] hub 4-0:1.0: 2 ports detected
[    2.541657] usbcore: registered new interface driver libusual
[    2.541705] usbcore: registered new interface driver usbserial
[    2.541719] USB Serial support registered for generic
[    2.541742] usbcore: registered new interface driver usbserial_generic
[    2.541745] usbserial: USB Serial Driver core
[    2.541806] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.544698] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.544705] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.544848] mice: PS/2 mouse device common for all mice
[    2.545081] rtc_cmos 00:01: RTC can wake from S4
[    2.545134] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.545152] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.545253] device-mapper: uevent: version 1.0.3
[    2.545408] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.545471] device-mapper: multipath: version 1.0.5 loaded
[    2.545475] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.545577] EISA: Probing bus 0 at eisa.0
[    2.545587] Cannot allocate resource for EISA slot 1
[    2.545590] Cannot allocate resource for EISA slot 2
[    2.545594] Cannot allocate resource for EISA slot 3
[    2.545617] EISA: Detected 0 cards.
[    2.545706] cpuidle: using governor ladder
[    2.545792] cpuidle: using governor menu
[    2.546469] TCP cubic registered
[    2.546613] NET: Registered protocol family 10
[    2.547158] lo: Disabled Privacy Extensions
[    2.547590] NET: Registered protocol family 17
[    2.547614] Bluetooth: L2CAP ver 2.11
[    2.547616] Bluetooth: L2CAP socket layer initialized
[    2.547620] Bluetooth: SCO (Voice Link) ver 0.6
[    2.547622] Bluetooth: SCO socket layer initialized
[    2.547658] Bluetooth: RFCOMM socket layer initialized
[    2.547668] Bluetooth: RFCOMM TTY layer initialized
[    2.547671] Bluetooth: RFCOMM ver 1.10
[    2.547721] IO APIC resources could be not be allocated.
[    2.547772] Using IPI No-Shortcut mode
[    2.547884] registered taskstats version 1
[    2.548063]   Magic number: 5:591:874
[    2.548162] rtc_cmos 00:01: setting system clock to 2009-04-07 07:51:13 UTC (1239090673)
[    2.548167] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.548169] EDD information not available.
[    2.548536] Freeing unused kernel memory: 532k freed
[    2.548699] Write protecting the kernel text: 4128k
[    2.548755] Write protecting the kernel read-only data: 1532k
[    2.773642] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.124058] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    3.265282] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.265330] 8139cp 0000:02:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.269472] 8139too Fast Ethernet driver 0.9.28
[    3.269521] 8139too 0000:02:08.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.270633] eth0: RealTek RTL8139 at 0x3000, 00:03:25:20:31:61, IRQ 10
[    3.270636] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.284610] ohci1394 0000:02:07.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.337436] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.351105] b43-pci-bridge 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.354553] ssb: Sonics Silicon Backplane found on PCI device 0000:02:09.0
[    3.381083] usb 3-2: configuration #1 chosen from 1 choice
[    3.626531] usbcore: registered new interface driver hiddev
[    3.630892] Marking TSC unstable due to TSC halts in idle
[    3.659568] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6
[    3.660005] generic-usb 0003:045E:00D1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.1-2/input0
[    3.660062] usbcore: registered new interface driver usbhid
[    3.660068] usbhid: v2.6:USB HID core driver
[    3.736960] PM: Starting manual resume from disk
[    3.736965] PM: Resume from partition 8:5
[    3.736968] PM: Checking hibernation image.
[    3.737156] PM: Resume from disk failed.
[    3.780101] kjournald starting.  Commit interval 5 seconds
[    3.780117] EXT3-fs: mounted filesystem with ordered data mode.
[    4.620187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0003252135027a69]
[   11.576545] udev: starting version 140
[   12.069468] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.089995] acpi device:05: registered as cooling_device1
[   12.090231] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input7
[   12.120214] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   12.428597] intel_rng: FWH not detected
[   12.617565] Linux agpgart interface v0.103
[   12.632328] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   12.678556] yenta_cardbus 0000:02:07.0: CardBus bridge found [161f:203a]
[   12.765870] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.804904] yenta_cardbus 0000:02:07.0: ISA IRQ mask 0x0090, PCI irq 11
[   12.804910] yenta_cardbus 0000:02:07.0: Socket status: 30000006
[   12.804916] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   12.804927] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   12.804932] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   12.805244] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   12.805249] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
[   12.805791] yenta_cardbus 0000:02:07.1: CardBus bridge found [161f:203a]
[   12.822677] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   12.823006] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[   12.825870] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   12.901478] iTCO_vendor_support: vendor-support=0
[   12.904241] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.904402] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   12.904511] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.925672] cfg80211: Calling CRDA to update world regulatory domain
[   12.933003] yenta_cardbus 0000:02:07.1: ISA IRQ mask 0x0090, PCI irq 10
[   12.933009] yenta_cardbus 0000:02:07.1: Socket status: 30000006
[   12.933015] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   12.933028] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   12.933033] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: clean.
[   12.933346] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   12.933350] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
[   13.090918] cfg80211: World regulatory domain updated:
[   13.090925] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.090929] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.090933] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.090937] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.090941] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.090944] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.243939] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.245638] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.246393] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.246989] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.247779] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.392282] b43-phy0: Broadcom 4306 WLAN found
[   13.448414] phy0: Selected rate control algorithm 'pid'
[   13.552177] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   13.672924] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   13.674596] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.675312] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   13.675906] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   13.676728] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   13.677543] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   13.677771] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   13.711743] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   13.747460] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.604047] intel8x0_measure_ac97_clock: measured 55443 usecs
[   14.604052] intel8x0: clocking to 48000
[   14.934729] lp: driver loaded but no devices found
[   15.158598] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   15.756295] EXT3 FS on sda1, internal journal
[   17.013319] type=1505 audit(1239090687.963:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1982
[   17.095970] type=1505 audit(1239090688.043:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1986
[   17.096243] type=1505 audit(1239090688.047:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1986
[   17.096330] type=1505 audit(1239090688.047:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1986
[   17.096404] type=1505 audit(1239090688.047:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1986
[   17.330034] type=1505 audit(1239090688.279:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1991
[   17.330417] type=1505 audit(1239090688.279:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1991
[   17.375469] type=1505 audit(1239090688.323:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1995
[   21.542845] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.542850] Bluetooth: BNEP filters: protocol multicast
[   21.585302] Bridge firewalling registered
[   24.036619] ppdev: user-space parallel port driver
[   25.409440] [drm] Initialized drm 1.1.0 20060810
[   25.519992] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[   25.520001] pci 0000:00:02.0: setting latency timer to 64
[   25.520813] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   25.608714] [drm:i915_setparam] *ERROR* unknown parameter 4
[   25.608747] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   26.761711] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   28.049208] eth0: link down
[   28.049552] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.203383] input: b43-phy0 as /devices/virtual/input/input10
[   28.236064] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.298090] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.298098] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   28.316339] input: b43-phy0 as /devices/virtual/input/input11
[   28.353756] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.357547] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.357555] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  125.299745] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  293.213860] input: b43-phy0 as /devices/virtual/input/input12
[  293.272114] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  293.279467] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  293.279475] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  331.445815] input: b43-phy0 as /devices/virtual/input/input13
[  331.460093] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  331.468791] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  331.468800] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  331.516089] input: b43-phy0 as /devices/virtual/input/input14
[  331.578591] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  331.581651] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  331.581658] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  401.518075] input: b43-phy0 as /devices/virtual/input/input15
[  401.538556] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  401.629890] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  401.629900] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[ 2476.691626] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 3844.970925] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 7322.120072] usb 3-2: USB disconnect, address 2
[ 7322.468045] usb 3-2: new low speed USB device using uhci_hcd and address 3
[ 7322.644923] usb 3-2: configuration #1 chosen from 1 choice
[ 7322.668333] usb 3-2: can't set config #1, error -71
[ 7322.864071] hub 3-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 7322.864080] usb 3-2: USB disconnect, address 3
[ 7323.104062] usb 3-2: new low speed USB device using uhci_hcd and address 4
[ 7323.286813] usb 3-2: configuration #1 chosen from 1 choice
[ 7323.358699] generic-usb: probe of 0003:045E:00D1.0002 failed with error -71
[ 7323.358892] usb 3-2: USB disconnect, address 4
[ 7324.096045] usb 3-2: new low speed USB device using uhci_hcd and address 5
[ 7324.277642] usb 3-2: configuration #1 chosen from 1 choice
[ 7324.357362] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input16
[ 7324.368676] generic-usb 0003:045E:00D1.0003: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.1-2/input0
[ 7451.937909] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 7451.937915] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 7451.937919] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
**angie@angie-laptop:~$ sudo lshw -C network**
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:20:31:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:c6:42:5e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:28:73:83:f2:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
**angie@angie-laptop:~$ iwlist scan wlan0**
iwlist: unknown command `wlan0' (check 'iwlist --help').
**angie@angie-laptop:~$ iwlist**
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
**angie@angie-laptop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.


lwlan0     Failed to read scan data : Resource temporarily unavailable

pan0      Interface doesn't support scanning.

angie@angie-laptop:~$ 
**angie@angie-laptop:~$ lsb_release -d**
Description:	Ubuntu jaunty (development branch)
**angie@angie-laptop:~$ uname -mr**
2.6.28-11-generic i686
**angie@angie-laptop:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                                                           [ OK ] 
angie@angie-laptop:~$

---

### Post by Ayuthia on 2009-04-09
> **dax702 said:**
> 
[   28.353756] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.357547] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.357555] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  125.299745] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  293.213860] input: b43-phy0 as /devices/virtual/input/input12
[  293.272114] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  293.279467] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  293.279475] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  331.445815] input: b43-phy0 as /devices/virtual/input/input13
[  331.460093] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  331.468791] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  331.468800] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  331.516089] input: b43-phy0 as /devices/virtual/input/input14
[  331.578591] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  331.581651] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  331.581658] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  401.518075] input: b43-phy0 as /devices/virtual/input/input15
[  401.538556] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  401.629890] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  401.629900] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).

From your dmesg information above, it looks like you have not installed the firmware for your computer.  If you have a working internet connection in Ubuntu, go to System->Administration->Hardware Drivers and select the Broadcom b43 option.  It will download the firmware for you and cut out the pieces of firmware it needs to make your card work.

---

### Post by dax702 on 2009-04-09
I finally got it to work, but only after hooking it up to the internet via a wired connection. Thank you for the reply :p

---

