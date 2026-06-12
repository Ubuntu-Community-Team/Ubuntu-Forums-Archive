---
title: "PlayTV Pro /w conexant bt878 chipset"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by sefs on 2008-01-05
Hi how do i install this card.

I am on gutsy....

I see in ls mod that bttv is listed and bt878 is also listed
```

Module                  Size  Used by
bt878                  10920  0 
bttv                  174260  1 bt878
video_buf              25604  1 bttv
ir_common              34436  1 bttv
compat_ioctl32          1408  1 bttv
i2c_algo_bit            6532  1 bttv
btcx_risc               5000  1 bttv
tveeprom               15888  1 bttv
i2c_core               25104  5 nvidia,i2c_viapro,bttv,i2c_algo_bit,tveeprom
videodev               28288  1 bttv
v4l2_common            17536  2 bttv,videodev
v4l1_compat            14468  2 bttv,videodev

```

also a lspci gives

```

00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

```

How do I actually get to watch TV now.  And get this card up and working.

Thanks.

---

### Post by Gourgi on 2008-01-06
i have the same card, different revision
i'm able to watch tv
i use tvtime
install it through add/remove applications

---

### Post by sefs on 2008-01-06
I have tvtime installed....

Did you have to do anything with this? like put it in a file anywhere?

```

modprobe bttv card=37 tuner=5 radio=1

```

Or did you just plug in and installed tvtime and it worked.

Your help is much appreciated.

Thanks.

> **Gourgi said:**
> i have the same card, different revision
i'm able to watch tv
i use tvtime
install it through add/remove applications

---

### Post by Gourgi on 2008-01-06
i have put this in a script in order to make it work
```
#!/bin/bash

rmmod bt878
rmmod bttv
modprobe bttv radio=1 card=70 tuner=5
```
i run this script at every startup manually because it needs superuser passwd and putting it in startup sessions didn't work
i think i have to put the modules options somewhere in the /etc/modules or modprobe,d folder but i couldn't make it to work.
what i simple do in the script above is ;
firstly remove the bt878 module , then remove the bttv module and then enable the bttv module again using my options.
the problem is that if you try to remove only the bttv module , it says it is in use, that's why i rermove bt878 module first.
try the script above using your module options

i hope i helped you :popcorn:

---

### Post by sefs on 2008-01-07
I actually have to use card=37 as mine is not revision 4.

EDIT: Actually I think I have the same card as you as I look directly at the card and it has printed in brackets (rev 4C)

I want to compare dmesg output with you...

The part of the dmesg outpout i see associated with bttv is below, in some parts it seems the card is being set up but at the very end it says failure of some sort.  Can you post your dmesg so that I can see what it should look like for a successful setup.

Thanks.

```

[   35.582152] bttv: driver version 0.9.17 loaded
[   35.582157] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   35.582211] bttv: Bt8xx card found (0).
[   35.582224] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   35.582236] bttv0: Bt878 (rev 2) at 0000:00:09.0, irq: 16, latency: 32, mmio: 0xfa002000
[   35.582245] bttv0: using: Prolink PixelView PlayTV pro [card=37,insmod option]
[   35.582273] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   35.808838] nvidia: module license 'NVIDIA' taints kernel.
[   36.536140] Real Time Clock Driver v1.12ac
[   36.641382] bttv0: using tuner=5
[   36.641388] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   36.916162] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   37.104541] bttv0: i2c: checking for TDA9887 @ 0x86... rtusb init ====>
[   37.160530] idVendor = 0x148f, idProduct = 0x2573 
[   37.174063] not found
[   37.230083] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   37.230116] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   37.230121] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   37.236870] bttv0: registered device video0
[   37.236899] bttv0: registered device vbi0
[   37.236928] bttv0: registered device radio0
[   37.236947] bttv0: PLL: 28636363 => 35468950 .. ok
[   37.285684] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xe100, speed 1046kHz
[   37.285976] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   37.286234] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   37.300531] bt878: AUDIO driver version 0.0.0 loaded
[   37.300570] bt878: Bt878 AUDIO function found (0).
[   37.300580] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 16
[   37.300586] bt878_probe: card id=[0x0], Unknown card.
[   37.300588] Exiting..
[   37.300592] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[   37.300627] bt878: probe of 0000:00:09.1 failed with error -22

```

---

### Post by sefs on 2008-01-07
Another thing Gourgi you use tuner = 5.  Is this if you have a PAL set up?

I am ntsc ... does that mean i have to go with the tuner =2?

---

### Post by Gourgi on 2008-01-07
> **sefs said:**
> Another thing Gourgi you use tuner = 5.  Is this if you have a PAL set up?

I am ntsc ... does that mean i have to go with the tuner =2?

yes i use PAL 
i think 5 stands for PAL , i don't know about ntsc 
from a quick check on google i found tuner = 2 is for ntsc
as for dmesg, i 'll post it as soon as i go back home

---

### Post by Gourgi on 2008-01-08
sorry for keeping you waitng 
here is my dmesg before running my script
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=79e75bb3-0886-473b-9696-94e80b631d33 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F92D0 checksum 0
[    0.000000] ACPI: RSDP 000F92D0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 6384 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9640, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF9580, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524272
[    0.000000] On node 0 totalpages: 524175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1140 pages reserved
[    0.000000]   DMA zone: 2803 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515868
[    0.000000] Kernel command line: root=UUID=79e75bb3-0886-473b-9696-94e80b631d33 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   21.087845] time.c: Detected 1809.300 MHz processor.
[   21.089725] Console: colour VGA+ 80x25
[   21.089742] Checking aperture...
[   21.089745] CPU 0: aperture @ c028000000 size 32 MB
[   21.089747] Aperture too small (32 MB)
[   21.094899] No AGP bridge found
[   21.117253] Memory: 2056140k/2097088k available (2274k kernel code, 40560k reserved, 1181k data, 296k init)
[   21.117301] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.193667] Calibrating delay using timer specific routine.. 3620.79 BogoMIPS (lpj=7241597)
[   21.193700] Security Framework v1.0.0 initialized
[   21.193706] SELinux:  Disabled at boot.
[   21.193874] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.195356] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.196080] Mount-cache hash table entries: 256
[   21.196213] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.196216] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.196218] CPU 0/0 -> Node 0
[   21.196220] CPU: Physical Processor ID: 0
[   21.196222] CPU: Processor Core ID: 0
[   21.196239] SMP alternatives: switching to UP code
[   21.196514] Early unpacking initramfs... done
[   21.517182] ACPI: Core revision 20070126
[   21.517243] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.561940] Using local APIC timer interrupts.
[   21.617119] result 12564592
[   21.617120] Detected 12.564 MHz APIC timer.
[   21.621018] SMP alternatives: switching to SMP code
[   21.621130] Booting processor 1/2 APIC 0x1
[   21.631291] Initializing CPU#1
[   21.708875] Calibrating delay using timer specific routine.. 3618.71 BogoMIPS (lpj=7237438)
[   21.708882] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.708884] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.708887] CPU 1/1 -> Node 0
[   21.708889] CPU: Physical Processor ID: 0
[   21.708890] CPU: Processor Core ID: 1
[   21.709013] Dual Core AMD Opteron(tm) Processor 165    stepping 02
[   21.712813] Brought up 2 CPUs
[   22.775887] migration_cost=348
[   22.776003] NET: Registered protocol family 16
[   22.776084] ACPI: bus type pci registered
[   22.776090] PCI: Using configuration type 1
[   22.777352] ACPI: EC: Look up EC in DSDT
[   22.784798] ACPI: Interpreter enabled
[   22.784801] ACPI: (supports S0 S1 S4 S5)
[   22.784818] ACPI: Using IOAPIC for interrupt routing
[   22.795115] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.795127] PCI: Probing PCI hardware (bus 00)
[   22.795625] PCI: Transparent bridge - 0000:00:09.0
[   22.795903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.796213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.862560] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.862772] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.862989] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.863200] ACPI: PCI Interrupt Link [LNK4] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.863410] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.863621] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.863831] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.864042] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.864253] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.864464] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.864675] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.864885] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.865095] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.865314] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.865532] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.865750] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.865982] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.866206] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   22.866430] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.866656] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   22.866807] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.867040] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.867270] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.867498] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.867727] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   22.867955] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   22.868184] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.868412] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.868642] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.868878] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.869114] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.869350] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.869461] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.869471] pnp: PnP ACPI init
[   22.869479] ACPI: bus type pnp registered
[   22.875165] pnp: PnP ACPI: found 14 devices
[   22.875167] ACPI: ACPI bus type pnp unregistered
[   22.875219] PCI: Using ACPI for IRQ routing
[   22.875223] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.875290] NET: Registered protocol family 8
[   22.875292] NET: Registered protocol family 20
[   22.875394] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
[   22.875397] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[   22.875400] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[   22.875403] pnp: 00:01: ioport range 0x4480-0x44ff has been reserved
[   22.875406] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[   22.875409] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[   22.875413] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   22.875423] pnp: 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.875428] pnp: 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[   22.875431] pnp: 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[   22.875434] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   22.875437] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   22.875712] PCI: Bridge: 0000:00:09.0
[   22.875714]   IO window: d000-dfff
[   22.875718]   MEM window: fde00000-fdefffff
[   22.875721]   PREFETCH window: fdf00000-fdffffff
[   22.875724] PCI: Bridge: 0000:00:0b.0
[   22.875726]   IO window: c000-cfff
[   22.875729]   MEM window: fdd00000-fddfffff
[   22.875732]   PREFETCH window: fdc00000-fdcfffff
[   22.875735] PCI: Bridge: 0000:00:0c.0
[   22.875738]   IO window: b000-bfff
[   22.875741]   MEM window: fdb00000-fdbfffff
[   22.875744]   PREFETCH window: fda00000-fdafffff
[   22.875747] PCI: Bridge: 0000:00:0d.0
[   22.875749]   IO window: a000-afff
[   22.875752]   MEM window: fd900000-fd9fffff
[   22.875755]   PREFETCH window: fd800000-fd8fffff
[   22.875760] PCI: Bridge: 0000:00:0e.0
[   22.875762]   IO window: 9000-9fff
[   22.875765]   MEM window: f4000000-fbffffff
[   22.875769]   PREFETCH window: d8000000-dfffffff
[   22.875775] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.875782] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.875788] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.875794] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.875799] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.875811] NET: Registered protocol family 2
[   22.878930] Time: acpi_pm clocksource has been installed.
[   22.914814] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   22.915596] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   22.919802] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.920514] TCP: Hash tables configured (established 262144 bind 65536)
[   22.920517] TCP reno registered
[   22.934840] checking if image is initramfs... it is
[   23.565043] Freeing initrd memory: 7194k freed
[   23.570606] audit: initializing netlink socket (disabled)
[   23.570622] audit(1199805748.440:1): initialized
[   23.572763] VFS: Disk quotas dquot_6.5.1
[   23.572813] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.572893] io scheduler noop registered
[   23.572895] io scheduler anticipatory registered
[   23.572897] io scheduler deadline registered
[   23.572994] io scheduler cfq registered (default)
[   23.602254] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   23.602264] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602271] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   23.602278] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602283] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   23.602290] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602296] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   23.602303] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602313] Boot video device is 0000:05:00.0
[   23.602457] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.602477] assign_interrupt_mode Found MSI capability
[   23.602480] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.602545] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.602563] assign_interrupt_mode Found MSI capability
[   23.602566] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.602623] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.602640] assign_interrupt_mode Found MSI capability
[   23.602643] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.602696] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.602714] assign_interrupt_mode Found MSI capability
[   23.602716] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.628160] Real Time Clock Driver v1.12ac
[   23.628261] Linux agpgart interface v0.102 (c) Dave Jones
[   23.628263] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.628348] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.628887] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.629616] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.629753] input: Macintosh mouse button emulation as /class/input/input0
[   23.629829] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.632197] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.632202] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.632354] mice: PS/2 mouse device common for all mice
[   23.632484] TCP cubic registered
[   23.632540] NET: Registered protocol family 1
[   23.632744] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.632755] Freeing unused kernel memory: 296k freed
[   23.659211] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.818936] AppArmor: AppArmor initialized<5>audit(1199805749.688:2):  type=1505 info="AppArmor initialized" pid=1263
[   24.824185] fuse init (API version 7.8)
[   24.828464] Failure registering capabilities with primary security module.
[   24.858860] ACPI: Fan [FAN] (on)
[   24.864098] ACPI: Thermal Zone [THRM] (22 C)
[   25.343410] usbcore: registered new interface driver usbfs
[   25.343434] usbcore: registered new interface driver hub
[   25.343459] usbcore: registered new device driver usb
[   25.344114] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.344531] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   25.344539] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   25.344982] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.344989] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   25.345128] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   25.345148] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   25.403937] SCSI subsystem initialized
[   25.409120] libata version 2.21 loaded.
[   25.413473] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   25.439905] usb usb1: configuration #1 chosen from 1 choice
[   25.439940] hub 1-0:1.0: USB hub found
[   25.439949] hub 1-0:1.0: 10 ports detected
[   25.493973] FDC 0 is a post-1991 82077
[   25.547092] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   25.547101] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   25.548062] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   25.548069] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   25.548379] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   25.548408] ehci_hcd 0000:00:02.1: debug port 1
[   25.548412] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   25.548423] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   25.548429] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.548818] usb usb2: configuration #1 chosen from 1 choice
[   25.548988] hub 2-0:1.0: USB hub found
[   25.548995] hub 2-0:1.0: 10 ports detected
[   25.655027] sata_nv 0000:00:07.0: version 3.4
[   25.655496] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   25.655504] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   25.655509] sata_nv 0000:00:07.0: Using ADMA mode
[   25.655940] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.656103] scsi0 : sata_nv
[   25.656153] scsi1 : sata_nv
[   25.656232] ata1: SATA max UDMA/133 cmd 0xffffc20000aa6480 ctl 0xffffc20000aa64a0 bmdma 0x000000000001f600 irq 21
[   25.656238] ata2: SATA max UDMA/133 cmd 0xffffc20000aa6580 ctl 0xffffc20000aa65a0 bmdma 0x000000000001f608 irq 21
[   26.125331] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.134395] ata1.00: ATA-7: Maxtor 7V300F0, VA111630, max UDMA/133
[   26.134398] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.154352] ata1.00: configured for UDMA/133
[   26.468737] ata2: SATA link down (SStatus 0 SControl 300)
[   26.468828] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   26.468835] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   26.469385] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   26.469393] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   26.469398] sata_nv 0000:00:08.0: Using ADMA mode
[   26.469751] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   26.469843] scsi2 : sata_nv
[   26.469911] scsi3 : sata_nv
[   26.469993] ata3: SATA max UDMA/133 cmd 0xffffc20000aa8480 ctl 0xffffc20000aa84a0 bmdma 0x000000000001f100 irq 20
[   26.469998] ata4: SATA max UDMA/133 cmd 0xffffc20000aa8580 ctl 0xffffc20000aa85a0 bmdma 0x000000000001f108 irq 20
[   26.871976] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   26.939936] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.948973] ata3.00: ATA-7: Maxtor 7V300F0, VA111630, max UDMA/133
[   26.948976] ata3.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.968935] ata3.00: configured for UDMA/133
[   27.075096] usb 1-1: configuration #1 chosen from 1 choice
[   27.283347] ata4: SATA link down (SStatus 0 SControl 300)
[   27.283442] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   27.283449] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.284272] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   27.284276] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   27.284282] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   27.284291] forcedeth: using HIGHDMA
[   27.383174] usb 1-7: new low speed USB device using ohci_hcd and address 3
[   27.640126] usb 1-7: configuration #1 chosen from 1 choice
[   27.806697] eth0: forcedeth.c: subsystem: 01462:7100 bound to 0000:00:0a.0
[   27.811377] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.811382] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.811933] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   27.811950] NFORCE-CK804: chipset revision 242
[   27.811952] NFORCE-CK804: not 100% native mode: will probe irqs later
[   27.811958] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   27.811965]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[   27.811974]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[   27.811981] Probing IDE interface ide0...
[   27.821209] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   27.821223] sd 0:0:0:0: [sda] Write Protect is off
[   27.821226] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.821240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.821290] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   27.821298] sd 0:0:0:0: [sda] Write Protect is off
[   27.821301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.821314] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.821319]  sda: sda1 sda2 < sda5 >
[   27.854038] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.854805] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   27.854816] sd 2:0:0:0: [sdb] Write Protect is off
[   27.854819] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.854833] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.854880] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   27.854888] sd 2:0:0:0: [sdb] Write Protect is off
[   27.854890] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.854902] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.854907]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[   27.901728] sd 2:0:0:0: [sdb] Attached SCSI disk
[   27.905198] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.905221] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.950216] usb 1-8: new full speed USB device using ohci_hcd and address 4
[   28.143072] Attempting manual resume
[   28.143076] swsusp: Resume From Partition 8:18
[   28.143078] PM: Checking swsusp image.
[   28.143230] PM: Resume from disk failed.
[   28.145291] usb 1-8: configuration #1 chosen from 1 choice
[   28.148380] hub 1-8:1.0: USB hub found
[   28.149411] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[   28.149417] ReiserFS: sdb1: using ordered data mode
[   28.151178] hub 1-8:1.0: 4 ports detected
[   28.156593] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   28.157770] ReiserFS: sdb1: checking transaction log (sdb1)
[   28.201321] ReiserFS: sdb1: Using r5 hash to sort names
[   28.283954] usbcore: registered new interface driver hiddev
[   28.289098] input: PS/2+USB Mouse as /class/input/input2
[   28.289119] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:02.0-1
[   28.306929] hiddev96: USB HID v1.11 Device [OMRON 87XXUPS] on usb-0000:00:02.0-7
[   28.306938] usbcore: registered new interface driver usbhid
[   28.306941] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.549270] hda: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[   29.220469] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.221736] Probing IDE interface ide1...
[   29.958838] hdc: LITE-ON LTR-24102B, ATAPI CD/DVD-ROM drive
[   30.294312] ide1 at 0x170-0x177,0x376 on irq 15
[   30.294887] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   30.294897] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   30.348008] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.631952] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000099bb70]
[   34.356401] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   34.356432] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   34.788017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.815559] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.859734] Linux video capture interface: v2.00
[   34.967270] bttv: driver version 0.9.17 loaded
[   34.967275] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   34.967335] bttv: Bt8xx card found (0).
[   34.967644] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   34.967652] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   34.967663] bttv0: Bt878 (rev 17) at 0000:01:06.0, irq: 16, latency: 32, mmio: 0xfdfff000
[   34.967670] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   34.967699] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   34.972055] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[   34.972060] bttv0: using tuner=-1
[   34.972062] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   34.972552] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   34.973043] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   34.973534] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   34.974077] bttv0: registered device video0
[   34.974107] bttv0: registered device vbi0
[   35.248852] nvidia: module license 'NVIDIA' taints kernel.
[   35.504883] bt878: AUDIO driver version 0.0.0 loaded
[   35.505185] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   35.505195] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   35.505203] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   35.505383] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.07  Thu Dec 13 18:34:01 PST 2007
[   35.505320] bt878: Bt878 AUDIO function found (0).
[   35.505343] ACPI: PCI Interrupt 0000:01:06.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   35.505349] bt878_probe: card id=[0x0], Unknown card.
[   35.505351] Exiting..
[   35.505355] ACPI: PCI interrupt for device 0000:01:06.1 disabled
[   35.505360] bt878: probe of 0000:01:06.1 failed with error -22
[   35.513069] usbcore: registered new interface driver xpad
[   35.513074] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   35.574149] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   35.576841] parport_pc 00:09: reported by Plug and Play ACPI
[   35.576886] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   35.577713] input: PC Speaker as /class/input/input4
[   35.641478] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.641488] Uniform CD-ROM driver Revision: 3.20
[   35.650694] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.861179] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   35.861200] snd-ca0106: Model 1009 Rev 00000000 Serial 10091462
[   36.747617] lp0: using parport0 (interrupt-driven).
[   36.817773] w83627hf: Found W83627THF chip at 0x290
[   36.819194] w83627hf w83627hf.656: Reading VID from GPIO5
[   36.846015] Adding 522104k swap on /dev/sdb2.  Priority:-1 extents:1 across:522104k
[   44.058935] kjournald starting.  Commit interval 5 seconds
[   44.059037] EXT3 FS on sdb3, internal journal
[   44.059042] EXT3-fs: mounted filesystem with ordered data mode.
[   45.309659] No dock devices found.
[   45.345670] input: Power Button (FF) as /class/input/input5
[   45.345692] ACPI: Power Button (FF) [PWRF]
[   45.345735] input: Power Button (CM) as /class/input/input6
[   45.345750] ACPI: Power Button (CM) [PWRB]
[   45.597358] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[   45.597317] powernow-k8: MP systems not supported by PSB BIOS structure
[   45.597395] powernow-k8: MP systems not supported by PSB BIOS structure
[   47.760125] Failure registering capabilities with primary security module.
[   47.944699] NET: Registered protocol family 10
[   47.944804] lo: Disabled Privacy Extensions
[   52.138258] NET: Registered protocol family 17
[   63.784429] UDF-fs: No VRS found
[   63.799325] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.855136] ISOFS: changing to secondary root
[   67.063212] eth0: no IPv6 routers present
```
i noticed the errors are same as yours

and here is dmesg after my script
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=79e75bb3-0886-473b-9696-94e80b631d33 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F92D0 checksum 0
[    0.000000] ACPI: RSDP 000F92D0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 6384 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9640, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF9580, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524272
[    0.000000] On node 0 totalpages: 524175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1140 pages reserved
[    0.000000]   DMA zone: 2803 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515868
[    0.000000] Kernel command line: root=UUID=79e75bb3-0886-473b-9696-94e80b631d33 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   21.087845] time.c: Detected 1809.300 MHz processor.
[   21.089725] Console: colour VGA+ 80x25
[   21.089742] Checking aperture...
[   21.089745] CPU 0: aperture @ c028000000 size 32 MB
[   21.089747] Aperture too small (32 MB)
[   21.094899] No AGP bridge found
[   21.117253] Memory: 2056140k/2097088k available (2274k kernel code, 40560k reserved, 1181k data, 296k init)
[   21.117301] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.193667] Calibrating delay using timer specific routine.. 3620.79 BogoMIPS (lpj=7241597)
[   21.193700] Security Framework v1.0.0 initialized
[   21.193706] SELinux:  Disabled at boot.
[   21.193874] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.195356] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.196080] Mount-cache hash table entries: 256
[   21.196213] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.196216] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.196218] CPU 0/0 -> Node 0
[   21.196220] CPU: Physical Processor ID: 0
[   21.196222] CPU: Processor Core ID: 0
[   21.196239] SMP alternatives: switching to UP code
[   21.196514] Early unpacking initramfs... done
[   21.517182] ACPI: Core revision 20070126
[   21.517243] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.561940] Using local APIC timer interrupts.
[   21.617119] result 12564592
[   21.617120] Detected 12.564 MHz APIC timer.
[   21.621018] SMP alternatives: switching to SMP code
[   21.621130] Booting processor 1/2 APIC 0x1
[   21.631291] Initializing CPU#1
[   21.708875] Calibrating delay using timer specific routine.. 3618.71 BogoMIPS (lpj=7237438)
[   21.708882] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.708884] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.708887] CPU 1/1 -> Node 0
[   21.708889] CPU: Physical Processor ID: 0
[   21.708890] CPU: Processor Core ID: 1
[   21.709013] Dual Core AMD Opteron(tm) Processor 165    stepping 02
[   21.712813] Brought up 2 CPUs
[   22.775887] migration_cost=348
[   22.776003] NET: Registered protocol family 16
[   22.776084] ACPI: bus type pci registered
[   22.776090] PCI: Using configuration type 1
[   22.777352] ACPI: EC: Look up EC in DSDT
[   22.784798] ACPI: Interpreter enabled
[   22.784801] ACPI: (supports S0 S1 S4 S5)
[   22.784818] ACPI: Using IOAPIC for interrupt routing
[   22.795115] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.795127] PCI: Probing PCI hardware (bus 00)
[   22.795625] PCI: Transparent bridge - 0000:00:09.0
[   22.795903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.796213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.862560] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.862772] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.862989] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.863200] ACPI: PCI Interrupt Link [LNK4] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   22.863410] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.863621] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.863831] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.864042] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.864253] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.864464] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.864675] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.864885] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.865095] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.865314] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.865532] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.865750] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.865982] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.866206] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   22.866430] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.866656] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   22.866807] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.867040] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.867270] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.867498] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.867727] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   22.867955] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   22.868184] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.868412] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.868642] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.868878] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.869114] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.869350] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.869461] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.869471] pnp: PnP ACPI init
[   22.869479] ACPI: bus type pnp registered
[   22.875165] pnp: PnP ACPI: found 14 devices
[   22.875167] ACPI: ACPI bus type pnp unregistered
[   22.875219] PCI: Using ACPI for IRQ routing
[   22.875223] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.875290] NET: Registered protocol family 8
[   22.875292] NET: Registered protocol family 20
[   22.875394] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
[   22.875397] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[   22.875400] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[   22.875403] pnp: 00:01: ioport range 0x4480-0x44ff has been reserved
[   22.875406] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[   22.875409] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[   22.875413] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   22.875423] pnp: 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.875428] pnp: 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[   22.875431] pnp: 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[   22.875434] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   22.875437] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   22.875712] PCI: Bridge: 0000:00:09.0
[   22.875714]   IO window: d000-dfff
[   22.875718]   MEM window: fde00000-fdefffff
[   22.875721]   PREFETCH window: fdf00000-fdffffff
[   22.875724] PCI: Bridge: 0000:00:0b.0
[   22.875726]   IO window: c000-cfff
[   22.875729]   MEM window: fdd00000-fddfffff
[   22.875732]   PREFETCH window: fdc00000-fdcfffff
[   22.875735] PCI: Bridge: 0000:00:0c.0
[   22.875738]   IO window: b000-bfff
[   22.875741]   MEM window: fdb00000-fdbfffff
[   22.875744]   PREFETCH window: fda00000-fdafffff
[   22.875747] PCI: Bridge: 0000:00:0d.0
[   22.875749]   IO window: a000-afff
[   22.875752]   MEM window: fd900000-fd9fffff
[   22.875755]   PREFETCH window: fd800000-fd8fffff
[   22.875760] PCI: Bridge: 0000:00:0e.0
[   22.875762]   IO window: 9000-9fff
[   22.875765]   MEM window: f4000000-fbffffff
[   22.875769]   PREFETCH window: d8000000-dfffffff
[   22.875775] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.875782] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.875788] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.875794] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.875799] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.875811] NET: Registered protocol family 2
[   22.878930] Time: acpi_pm clocksource has been installed.
[   22.914814] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   22.915596] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   22.919802] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.920514] TCP: Hash tables configured (established 262144 bind 65536)
[   22.920517] TCP reno registered
[   22.934840] checking if image is initramfs... it is
[   23.565043] Freeing initrd memory: 7194k freed
[   23.570606] audit: initializing netlink socket (disabled)
[   23.570622] audit(1199805748.440:1): initialized
[   23.572763] VFS: Disk quotas dquot_6.5.1
[   23.572813] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.572893] io scheduler noop registered
[   23.572895] io scheduler anticipatory registered
[   23.572897] io scheduler deadline registered
[   23.572994] io scheduler cfq registered (default)
[   23.602254] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   23.602264] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602271] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   23.602278] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602283] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   23.602290] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602296] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   23.602303] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.602313] Boot video device is 0000:05:00.0
[   23.602457] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.602477] assign_interrupt_mode Found MSI capability
[   23.602480] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.602545] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.602563] assign_interrupt_mode Found MSI capability
[   23.602566] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.602623] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.602640] assign_interrupt_mode Found MSI capability
[   23.602643] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.602696] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.602714] assign_interrupt_mode Found MSI capability
[   23.602716] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.628160] Real Time Clock Driver v1.12ac
[   23.628261] Linux agpgart interface v0.102 (c) Dave Jones
[   23.628263] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.628348] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.628887] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.629616] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.629753] input: Macintosh mouse button emulation as /class/input/input0
[   23.629829] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.632197] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.632202] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.632354] mice: PS/2 mouse device common for all mice
[   23.632484] TCP cubic registered
[   23.632540] NET: Registered protocol family 1
[   23.632744] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.632755] Freeing unused kernel memory: 296k freed
[   23.659211] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.818936] AppArmor: AppArmor initialized<5>audit(1199805749.688:2):  type=1505 info="AppArmor initialized" pid=1263
[   24.824185] fuse init (API version 7.8)
[   24.828464] Failure registering capabilities with primary security module.
[   24.858860] ACPI: Fan [FAN] (on)
[   24.864098] ACPI: Thermal Zone [THRM] (22 C)
[   25.343410] usbcore: registered new interface driver usbfs
[   25.343434] usbcore: registered new interface driver hub
[   25.343459] usbcore: registered new device driver usb
[   25.344114] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.344531] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   25.344539] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   25.344982] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.344989] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   25.345128] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   25.345148] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   25.403937] SCSI subsystem initialized
[   25.409120] libata version 2.21 loaded.
[   25.413473] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   25.439905] usb usb1: configuration #1 chosen from 1 choice
[   25.439940] hub 1-0:1.0: USB hub found
[   25.439949] hub 1-0:1.0: 10 ports detected
[   25.493973] FDC 0 is a post-1991 82077
[   25.547092] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   25.547101] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   25.548062] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   25.548069] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   25.548379] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   25.548408] ehci_hcd 0000:00:02.1: debug port 1
[   25.548412] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   25.548423] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   25.548429] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.548818] usb usb2: configuration #1 chosen from 1 choice
[   25.548988] hub 2-0:1.0: USB hub found
[   25.548995] hub 2-0:1.0: 10 ports detected
[   25.655027] sata_nv 0000:00:07.0: version 3.4
[   25.655496] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   25.655504] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   25.655509] sata_nv 0000:00:07.0: Using ADMA mode
[   25.655940] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.656103] scsi0 : sata_nv
[   25.656153] scsi1 : sata_nv
[   25.656232] ata1: SATA max UDMA/133 cmd 0xffffc20000aa6480 ctl 0xffffc20000aa64a0 bmdma 0x000000000001f600 irq 21
[   25.656238] ata2: SATA max UDMA/133 cmd 0xffffc20000aa6580 ctl 0xffffc20000aa65a0 bmdma 0x000000000001f608 irq 21
[   26.125331] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.134395] ata1.00: ATA-7: Maxtor 7V300F0, VA111630, max UDMA/133
[   26.134398] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.154352] ata1.00: configured for UDMA/133
[   26.468737] ata2: SATA link down (SStatus 0 SControl 300)
[   26.468828] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   26.468835] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   26.469385] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   26.469393] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   26.469398] sata_nv 0000:00:08.0: Using ADMA mode
[   26.469751] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   26.469843] scsi2 : sata_nv
[   26.469911] scsi3 : sata_nv
[   26.469993] ata3: SATA max UDMA/133 cmd 0xffffc20000aa8480 ctl 0xffffc20000aa84a0 bmdma 0x000000000001f100 irq 20
[   26.469998] ata4: SATA max UDMA/133 cmd 0xffffc20000aa8580 ctl 0xffffc20000aa85a0 bmdma 0x000000000001f108 irq 20
[   26.871976] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   26.939936] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.948973] ata3.00: ATA-7: Maxtor 7V300F0, VA111630, max UDMA/133
[   26.948976] ata3.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.968935] ata3.00: configured for UDMA/133
[   27.075096] usb 1-1: configuration #1 chosen from 1 choice
[   27.283347] ata4: SATA link down (SStatus 0 SControl 300)
[   27.283442] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   27.283449] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.284272] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   27.284276] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   27.284282] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   27.284291] forcedeth: using HIGHDMA
[   27.383174] usb 1-7: new low speed USB device using ohci_hcd and address 3
[   27.640126] usb 1-7: configuration #1 chosen from 1 choice
[   27.806697] eth0: forcedeth.c: subsystem: 01462:7100 bound to 0000:00:0a.0
[   27.811377] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.811382] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.811933] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   27.811950] NFORCE-CK804: chipset revision 242
[   27.811952] NFORCE-CK804: not 100% native mode: will probe irqs later
[   27.811958] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   27.811965]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[   27.811974]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[   27.811981] Probing IDE interface ide0...
[   27.821209] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   27.821223] sd 0:0:0:0: [sda] Write Protect is off
[   27.821226] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.821240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.821290] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   27.821298] sd 0:0:0:0: [sda] Write Protect is off
[   27.821301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.821314] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.821319]  sda: sda1 sda2 < sda5 >
[   27.854038] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.854805] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   27.854816] sd 2:0:0:0: [sdb] Write Protect is off
[   27.854819] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.854833] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.854880] sd 2:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
[   27.854888] sd 2:0:0:0: [sdb] Write Protect is off
[   27.854890] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.854902] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.854907]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[   27.901728] sd 2:0:0:0: [sdb] Attached SCSI disk
[   27.905198] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.905221] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.950216] usb 1-8: new full speed USB device using ohci_hcd and address 4
[   28.143072] Attempting manual resume
[   28.143076] swsusp: Resume From Partition 8:18
[   28.143078] PM: Checking swsusp image.
[   28.143230] PM: Resume from disk failed.
[   28.145291] usb 1-8: configuration #1 chosen from 1 choice
[   28.148380] hub 1-8:1.0: USB hub found
[   28.149411] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[   28.149417] ReiserFS: sdb1: using ordered data mode
[   28.151178] hub 1-8:1.0: 4 ports detected
[   28.156593] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   28.157770] ReiserFS: sdb1: checking transaction log (sdb1)
[   28.201321] ReiserFS: sdb1: Using r5 hash to sort names
[   28.283954] usbcore: registered new interface driver hiddev
[   28.289098] input: PS/2+USB Mouse as /class/input/input2
[   28.289119] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:02.0-1
[   28.306929] hiddev96: USB HID v1.11 Device [OMRON 87XXUPS] on usb-0000:00:02.0-7
[   28.306938] usbcore: registered new interface driver usbhid
[   28.306941] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.549270] hda: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[   29.220469] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.221736] Probing IDE interface ide1...
[   29.958838] hdc: LITE-ON LTR-24102B, ATAPI CD/DVD-ROM drive
[   30.294312] ide1 at 0x170-0x177,0x376 on irq 15
[   30.294887] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   30.294897] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   30.348008] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.631952] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000099bb70]
[   34.356401] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   34.356432] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   34.788017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.815559] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.859734] Linux video capture interface: v2.00
[   34.967270] bttv: driver version 0.9.17 loaded
[   34.967275] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   34.967335] bttv: Bt8xx card found (0).
[   34.967644] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   34.967652] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   34.967663] bttv0: Bt878 (rev 17) at 0000:01:06.0, irq: 16, latency: 32, mmio: 0xfdfff000
[   34.967670] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   34.967699] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   34.972055] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[   34.972060] bttv0: using tuner=-1
[   34.972062] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   34.972552] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   34.973043] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   34.973534] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   34.974077] bttv0: registered device video0
[   34.974107] bttv0: registered device vbi0
[   35.248852] nvidia: module license 'NVIDIA' taints kernel.
[   35.504883] bt878: AUDIO driver version 0.0.0 loaded
[   35.505185] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   35.505195] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   35.505203] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   35.505383] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.07  Thu Dec 13 18:34:01 PST 2007
[   35.505320] bt878: Bt878 AUDIO function found (0).
[   35.505343] ACPI: PCI Interrupt 0000:01:06.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   35.505349] bt878_probe: card id=[0x0], Unknown card.
[   35.505351] Exiting..
[   35.505355] ACPI: PCI interrupt for device 0000:01:06.1 disabled
[   35.505360] bt878: probe of 0000:01:06.1 failed with error -22
[   35.513069] usbcore: registered new interface driver xpad
[   35.513074] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   35.574149] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   35.576841] parport_pc 00:09: reported by Plug and Play ACPI
[   35.576886] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   35.577713] input: PC Speaker as /class/input/input4
[   35.641478] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.641488] Uniform CD-ROM driver Revision: 3.20
[   35.650694] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.861179] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   35.861200] snd-ca0106: Model 1009 Rev 00000000 Serial 10091462
[   36.747617] lp0: using parport0 (interrupt-driven).
[   36.817773] w83627hf: Found W83627THF chip at 0x290
[   36.819194] w83627hf w83627hf.656: Reading VID from GPIO5
[   36.846015] Adding 522104k swap on /dev/sdb2.  Priority:-1 extents:1 across:522104k
[   44.058935] kjournald starting.  Commit interval 5 seconds
[   44.059037] EXT3 FS on sdb3, internal journal
[   44.059042] EXT3-fs: mounted filesystem with ordered data mode.
[   45.309659] No dock devices found.
[   45.345670] input: Power Button (FF) as /class/input/input5
[   45.345692] ACPI: Power Button (FF) [PWRF]
[   45.345735] input: Power Button (CM) as /class/input/input6
[   45.345750] ACPI: Power Button (CM) [PWRB]
[   45.597358] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[   45.597317] powernow-k8: MP systems not supported by PSB BIOS structure
[   45.597395] powernow-k8: MP systems not supported by PSB BIOS structure
[   47.760125] Failure registering capabilities with primary security module.
[   47.944699] NET: Registered protocol family 10
[   47.944804] lo: Disabled Privacy Extensions
[   52.138258] NET: Registered protocol family 17
[   63.784429] UDF-fs: No VRS found
[   63.799325] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.855136] ISOFS: changing to secondary root
[   67.063212] eth0: no IPv6 routers present
[  873.629303] bttv0: unloading
[  873.646839] bttv: driver version 0.9.17 loaded
[  873.646845] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  873.647342] bttv: Bt8xx card found (0).
[  873.647356] bttv0: Bt878 (rev 17) at 0000:01:06.0, irq: 16, latency: 32, mmio: 0xfdfff000
[  873.647750] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[  873.647781] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[  873.649085] bttv0: using tuner=5
[  873.649255] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  873.649820] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  873.650863] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  873.685125] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  873.696169] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  873.696263] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  873.696357] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  873.708070] bttv0: registered device video0
[  873.708091] bttv0: registered device vbi0
[  873.708109] bttv0: registered device radio0
[  873.708128] bttv0: PLL: 28636363 => 35468950 .. ok
[  873.750228] input: bttv IR (card=70) as /class/input/input7
```

at fact the appended lines are these 
```
[  873.629303] bttv0: unloading
[  873.646839] bttv: driver version 0.9.17 loaded
[  873.646845] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  873.647342] bttv: Bt8xx card found (0).
[  873.647356] bttv0: Bt878 (rev 17) at 0000:01:06.0, irq: 16, latency: 32, mmio: 0xfdfff000
[  873.647750] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[  873.647781] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[  873.649085] bttv0: using tuner=5
[  873.649255] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  873.649820] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  873.650863] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  873.685125] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  873.696169] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  873.696263] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  873.696357] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  873.708070] bttv0: registered device video0
[  873.708091] bttv0: registered device vbi0
[  873.708109] bttv0: registered device radio0
[  873.708128] bttv0: PLL: 28636363 => 35468950 .. ok
[  873.750228] input: bttv IR (card=70) as /class/input/input7

```

i hope  this helps you.

---

### Post by sefs on 2008-01-08
Ok thanks very much i am getting the same thing.  I just now have to figure out why i am not getting any video.

---

### Post by nautilus on 2008-05-11
I have the exact same card and aside from some fiddling to get it working on one system (AMD Sempron(tm) Processor 3200+ / Linux hydway 2.6.18-5-k7 #1 SMP Fri Jun 1 01:26:37 UTC 2007 i686 GNU/Linux) without any problems changing kernels, I'm having a really rough time getting it going on this system: Pentium III (Coppermine) / Linux Server 2.6.20.4 #5 Tue Aug 7 23:51:31 MDT 2007 i686 GNU/Linux

Same sort of issue.  Everything 'works', same tuner type, same norm, same card type, same software, same frequency, same physical coaxial cable from the same source, and yet on box #2 i get no signal/no picture at all.  Permablue screen.

---

