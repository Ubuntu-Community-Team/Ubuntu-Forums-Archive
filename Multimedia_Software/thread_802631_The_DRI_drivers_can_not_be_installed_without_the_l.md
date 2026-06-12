---
title: "The DRI drivers can not be installed without the latest kernel modules"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Megalorian on 2008-05-21
I'm trying to install a driver for an integrated Intel graphic card. I get the following error when I run the install script. 

> DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.



How do I install the latest kernal modules?

---

### Post by roderick on 2008-05-21
any reason you are not using the drivers supplied with ubuntu? The supplied drivers are the same from the web site and are built and tested for you.

---

### Post by Megalorian on 2008-05-22
> **roderick said:**
> any reason you are not using the drivers supplied with ubuntu? The supplied drivers are the same from the web site and are built and tested for you.

I've been having a blank screen on login problem (See below thread)
[http://ubuntuforums.org/showthread.php?t=774253](http://ubuntuforums.org/showthread.php?t=774253)

It was one more thing I thought I would try.

---

### Post by roderick on 2008-05-22
This sounds more like a BIOS issue - where the BIOS is not properly reporting the card capabilities.

1) Is there a BIOS update available for your system?
2) You may need a custom DSDT (sometimes you can find someone with an exact model with a fixed DSDT you can download)
3) Have you tried forcing XAA mode in the xorg.conf?
4) Have you tried disabling compiz?

As a fist step, I would try disabling compiz.

Can you post your Xorg.0.log file? and the output of dmesg? I need these to help diagnose your issue further.

---

### Post by Megalorian on 2008-05-22
Here is the output from dmesg:

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fec9000 (usable)
[    0.000000]  BIOS-e820: 000000003fec9000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261833) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261833
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261833
[    0.000000] On node 0 totalpages: 261833
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32204 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3FEF0000, 0028 (r1 DELL    CPi R   27D30A06 ASL        61)
[    0.000000] ACPI: FACP 3FEF0400, 0074 (r1 DELL    CPi R   27D30A06 ASL        61)
[    0.000000] ACPI: DSDT 3FEF0C00, 25D8 (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEFF800, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:beda0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259788
[    0.000000] Kernel command line: root=UUID=3feee4bb-58ca-41da-8a83-8b25f787e2fe ro quiet
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0180f000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2392.370 MHz processor.
[    9.941602] Console: colour VGA+ 80x25
[    9.941608] console [tty0] enabled
[    9.942658] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.943694] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.981552] Memory: 1025832k/1047332k available (2157k kernel code, 20780k reserved, 998k data, 364k init, 129828k highmem)
[    9.981563] virtual kernel memory layout:
[    9.981564]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.981565]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.981566]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.981567]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.981569]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[    9.981570]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[    9.981571]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[    9.981575] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.981651] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.061678] Calibrating delay using timer specific routine.. 4789.18 BogoMIPS (lpj=9578371)
[   10.061731] Security Framework initialized
[   10.061747] SELinux:  Disabled at boot.
[   10.061774] AppArmor: AppArmor initialized
[   10.061780] Failure registering capabilities with primary security module.
[   10.061792] Mount-cache hash table entries: 512
[   10.062034] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   10.062051] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   10.062054] CPU: L2 cache: 512K
[   10.062058] CPU: Hyper-Threading is disabled
[   10.062061] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   10.062079] Compat vDSO mapped to ffffe000.
[   10.062103] Checking 'hlt' instruction... OK.
[   10.078203] SMP alternatives: switching to UP code
[   10.080278] Freeing SMP alternatives: 11k freed
[   10.080449] Early unpacking initramfs... done
[   10.452444] ACPI: Core revision 20070126
[   10.452509] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.453795] ACPI: setting ELCR to 0200 (from 0800)
[   10.454742] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   10.454750] SMP motherboard not detected.
[   10.454753] Local APIC not detected. Using dummy APIC emulation.
[   10.454810] Brought up 1 CPUs
[   10.454833] CPU0 attaching sched-domain:
[   10.454837]  domain 0: span 01
[   10.454839]   groups: 01
[   10.455088] net_namespace: 64 bytes
[   10.455103] Booting paravirtualized kernel on bare hardware
[   10.455799] Time: 14:10:07  Date: 05/22/08
[   10.455835] NET: Registered protocol family 16
[   10.456110] EISA bus registered
[   10.456129] ACPI: bus type pci registered
[   10.509295] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[   10.509298] PCI: Using configuration type 1
[   10.509300] Setting up standard PCI resources
[   10.511163] ACPI: EC: Look up EC in DSDT
[   10.514230] ACPI: Interpreter enabled
[   10.514236] ACPI: (supports S0 S1 S3 S4 S5)
[   10.514254] ACPI: Using PIC for interrupt routing
[   10.518947] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.519462] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.519464] * this clock source is slow. If you are sure your timer does not have
[   10.519465] * this bug, please use "acpi_pm_good" to disable the workaround
[   10.519516] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   10.519520] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   10.519828] PCI: Transparent bridge - 0000:00:1e.0
[   10.519907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.520205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   10.527073] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[   10.527183] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[   10.527290] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[   10.527396] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[   10.527491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.527602] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.527748] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.527791] pnp: PnP ACPI init
[   10.527803] ACPI: bus type pnp registered
[   10.537803] pnpacpi: exceeded the max number of IO resources: 40
[   10.537901] pnp: PnP ACPI: found 12 devices
[   10.537905] ACPI: ACPI bus type pnp unregistered
[   10.537911] PnPBIOS: Disabled by ACPI PNP
[   10.538210] PCI: Using ACPI for IRQ routing
[   10.538214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.553668] NET: Registered protocol family 8
[   10.553671] NET: Registered protocol family 20
[   10.553763] AppArmor: AppArmor Filesystem Enabled
[   10.557646] Time: tsc clocksource has been installed.
[   10.565697] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   10.565701] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   10.565704] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[   10.565707] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   10.565710] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved
[   10.565713] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved
[   10.565716] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[   10.565720] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   10.565729] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   10.565732] system 00:02: ioport range 0x800-0x805 has been reserved
[   10.565734] system 00:02: ioport range 0x808-0x80f has been reserved
[   10.565742] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[   10.565745] system 00:03: ioport range 0x806-0x807 has been reserved
[   10.565748] system 00:03: ioport range 0x810-0x85f has been reserved
[   10.565751] system 00:03: ioport range 0x860-0x87f has been reserved
[   10.565753] system 00:03: ioport range 0x880-0x8bf has been reserved
[   10.565756] system 00:03: ioport range 0x8c0-0x8df has been reserved
[   10.565759] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[   10.565769] system 00:08: ioport range 0x900-0x97f has been reserved
[   10.565778] system 00:0b: ioport range 0x7b0-0x7bb has been reserved
[   10.565781] system 00:0b: ioport range 0x7c0-0x7df has been reserved
[   10.565783] system 00:0b: ioport range 0xbb0-0xbbb has been reserved
[   10.565786] system 00:0b: ioport range 0xbc0-0xbdf has been reserved
[   10.565789] system 00:0b: ioport range 0xfb0-0xfbb has been reserved
[   10.565792] system 00:0b: ioport range 0xfc0-0xfdf has been reserved
[   10.565794] system 00:0b: ioport range 0x13b0-0x13bb has been reserved
[   10.565797] system 00:0b: ioport range 0x13c0-0x13df has been reserved
[   10.565800] system 00:0b: ioport range 0x17b0-0x17bb has been reserved
[   10.565803] system 00:0b: ioport range 0x17c0-0x17df has been reserved
[   10.565806] system 00:0b: ioport range 0x1bb0-0x1bbb has been reserved
[   10.565809] system 00:0b: ioport range 0x1bc0-0x1bdf has been reserved
[   10.565811] system 00:0b: ioport range 0x1fb0-0x1fbb has been reserved
[   10.565814] system 00:0b: ioport range 0x1fc0-0x1fdf has been reserved
[   10.565817] system 00:0b: ioport range 0x23b0-0x23bb has been reserved
[   10.565820] system 00:0b: ioport range 0x23c0-0x23df has been reserved
[   10.565822] system 00:0b: ioport range 0x27b0-0x27bb has been reserved
[   10.565825] system 00:0b: ioport range 0x27c0-0x27df has been reserved
[   10.565828] system 00:0b: ioport range 0x2bb0-0x2bbb has been reserved
[   10.565831] system 00:0b: ioport range 0x2bc0-0x2bdf has been reserved
[   10.565834] system 00:0b: ioport range 0x2fb0-0x2fbb has been reserved
[   10.565836] system 00:0b: ioport range 0x2fc0-0x2fdf has been reserved
[   10.565839] system 00:0b: ioport range 0x33b0-0x33bb has been reserved
[   10.565842] system 00:0b: ioport range 0x33c0-0x33df has been reserved
[   10.565845] system 00:0b: ioport range 0x37b0-0x37bb has been reserved
[   10.565848] system 00:0b: ioport range 0x37c0-0x37df has been reserved
[   10.565850] system 00:0b: ioport range 0x3bb0-0x3bbb has been reserved
[   10.565856] system 00:0b: ioport range 0x3bc0-0x3bdf has been reserved
[   10.565859] system 00:0b: ioport range 0x3fb0-0x3fbb has been reserved
[   10.565862] system 00:0b: ioport range 0x3fc0-0x3fdf has been reserved
[   10.565865] system 00:0b: ioport range 0x43b0-0x43bb has been reserved
[   10.565867] system 00:0b: ioport range 0x43c0-0x43df has been reserved
[   10.565870] system 00:0b: ioport range 0x47b0-0x47bb has been reserved
[   10.565873] system 00:0b: ioport range 0x47c0-0x47df has been reserved
[   10.565876] system 00:0b: ioport range 0x4bb0-0x4bbb has been reserved
[   10.565879] system 00:0b: ioport range 0x4bc0-0x4bdf has been reserved
[   10.565882] system 00:0b: ioport range 0x4fb0-0x4fbb has been reserved
[   10.565885] system 00:0b: ioport range 0x4fc0-0x4fdf has been reserved
[   10.565888] system 00:0b: ioport range 0x53b0-0x53bb has been reserved
[   10.565890] system 00:0b: ioport range 0x53c0-0x53df has been reserved
[   10.596439] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   10.596443]   IO window: 0000d000-0000d0ff
[   10.596448]   IO window: 0000d400-0000d4ff
[   10.596453]   PREFETCH window: f8000000-fbffffff
[   10.596458]   MEM window: 54000000-57ffffff
[   10.596462] PCI: Bridge: 0000:00:1e.0
[   10.596466]   IO window: d000-efff
[   10.596472]   MEM window: f8000000-fdffffff
[   10.596476]   PREFETCH window: disabled.
[   10.596493] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.596516] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[   10.596707] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   10.596711] PCI: setting IRQ 11 as level-triggered
[   10.596715] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.596738] NET: Registered protocol family 2
[   10.633758] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.634234] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.635629] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.636515] TCP: Hash tables configured (established 131072 bind 65536)
[   10.636521] TCP reno registered
[   10.645933] checking if image is initramfs... it is
[   11.097638] Switched to high resolution mode on CPU 0
[   11.380631] Freeing initrd memory: 7672k freed
[   11.381305] audit: initializing netlink socket (disabled)
[   11.381328] audit(1211465408.400:1): initialized
[   11.381598] highmem bounce pool size: 64 pages
[   11.383927] VFS: Disk quotas dquot_6.5.1
[   11.384031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.384218] io scheduler noop registered
[   11.384220] io scheduler anticipatory registered
[   11.384223] io scheduler deadline registered
[   11.384237] io scheduler cfq registered (default)
[   11.384254] Boot video device is 0000:00:02.0
[   11.384676] isapnp: Scanning for PnP cards...
[   11.737886] isapnp: No Plug & Play device found
[   11.776957] Real Time Clock Driver v1.12ac
[   11.777110] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.778693] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.778783] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.778914] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.779081] i8042.c: Warning: Keylock active.
[   11.781723] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.781730] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.785816] mice: PS/2 mouse device common for all mice
[   11.785980] EISA: Probing bus 0 at eisa.0
[   11.786022] EISA: Detected 0 cards.
[   11.786027] cpuidle: using governor ladder
[   11.786030] cpuidle: using governor menu
[   11.786162] NET: Registered protocol family 1
[   11.786200] Using IPI No-Shortcut mode
[   11.786255] registered taskstats version 1
[   11.786365]   Magic number: 8:746:182
[   11.786415]   hash matches device ttyr8
[   11.786515] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.786518] EDD information not available.
[   11.787067] Freeing unused kernel memory: 364k freed
[   11.789388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.042303] fuse init (API version 7.9)
[   12.072481] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.076559] ACPI: Thermal Zone [THM] (47 C)
[   12.517561] usbcore: registered new interface driver usbfs
[   12.517596] usbcore: registered new interface driver hub
[   12.525521] usbcore: registered new device driver usb
[   12.533529] USB Universal Host Controller Interface driver v3.0
[   12.533626] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.533643] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.533648] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.534049] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.534081] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   12.534269] usb usb1: configuration #1 chosen from 1 choice
[   12.534302] hub 1-0:1.0: USB hub found
[   12.534310] hub 1-0:1.0: 2 ports detected
[   12.637815] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.637822] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.637836] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.637841] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.637871] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.637902] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[   12.638054] usb usb2: configuration #1 chosen from 1 choice
[   12.638084] hub 2-0:1.0: USB hub found
[   12.638092] hub 2-0:1.0: 2 ports detected
[   12.741815] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.741821] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.741838] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.741843] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.741874] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.741904] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   12.742054] usb usb3: configuration #1 chosen from 1 choice
[   12.742084] hub 3-0:1.0: USB hub found
[   12.742092] hub 3-0:1.0: 2 ports detected
[   12.845875] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.845883] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.845900] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.845905] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.845941] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   12.849870] ehci_hcd 0000:00:1d.7: debug port 1
[   12.849878] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   12.849887] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6f7fc00
[   12.865407] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.865574] usb usb4: configuration #1 chosen from 1 choice
[   12.865606] hub 4-0:1.0: USB hub found
[   12.865615] hub 4-0:1.0: 6 ports detected
[   12.869730] SCSI subsystem initialized
[   12.957747] libata version 3.00 loaded.
[   12.971809] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.971825] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.971900] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.971919] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   12.974967] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[   12.974974] PCI: setting IRQ 7 as level-triggered
[   12.974979] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   13.033472] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[   13.033506] b44.c:v2.0
[   13.033540] ata_piix 0000:00:1f.1: version 2.12
[   13.033566] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.033632] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.040803] scsi0 : ata_piix
[   13.049778] scsi1 : ata_piix
[   13.049999] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   13.050003] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   13.053867] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:a8:45:79
[   13.369748] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[   13.541617] ata1.00: configured for UDMA/33
[   13.705987] ata2.00: ATA-6: FUJITSU MHT2060AH, 006C, max UDMA/100
[   13.705992] ata2.00: 117210240 sectors, multi 8: LBA
[   13.721804] ata2.00: configured for UDMA/100
[   13.727088] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[   13.727324] scsi 1:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 006C PQ: 0 ANSI: 5
[   13.917384] Driver 'sr' needs updating - please use bus_type methods
[   13.921821] Driver 'sd' needs updating - please use bus_type methods
[   13.938373] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   13.938380] Uniform CD-ROM driver Revision: 3.20
[   13.938459] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   13.938771] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.938789] sd 1:0:0:0: [sda] Write Protect is off
[   13.938792] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.944384] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.944465] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.944481] sd 1:0:0:0: [sda] Write Protect is off
[   13.944484] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.944507] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.944511]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   13.946007] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   14.022534]  sda1 sda2 sda3 < sda5 sda6 >
[   14.062047] sd 1:0:0:0: [sda] Attached SCSI disk
[   14.468225] Attempting manual resume
[   14.468231] swsusp: Resume From Partition 8:6
[   14.468233] PM: Checking swsusp image.
[   14.468514] PM: Resume from disk failed.
[   14.487627] EXT3-fs: INFO: recovery required on readonly filesystem.
[   14.487632] EXT3-fs: write access will be enabled during recovery.
[   14.600191] kjournald starting.  Commit interval 5 seconds
[   14.600213] EXT3-fs: recovery complete.
[   14.610092] EXT3-fs: mounted filesystem with ordered data mode.
[   25.900592] Linux agpgart interface v0.102
[   25.940319] agpgart: Detected an Intel 830M Chipset.
[   25.940435] agpgart: Detected 892K stolen memory.
[   25.987849] iTCO_vendor_support: vendor-support=0
[   26.024101] agpgart: AGP aperture is 128M @ 0xe0000000
[   26.024186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.028810] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   26.028866] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.071880] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.120625] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.224089] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   26.311787] intel_rng: FWH not detected
[   26.519904] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.971750] ACPI: Battery Slot [BAT0] (battery present)
[   27.239371] ACPI: AC Adapter [AC] (on-line)
[   27.239484] input: Lid Switch as /devices/virtual/input/input3
[   27.242518] ACPI: Lid Switch [LID]
[   27.242575] input: Power Button (CM) as /devices/virtual/input/input4
[   27.255694] ACPI: Power Button (CM) [PBTN]
[   27.255817] input: Sleep Button (CM) as /devices/virtual/input/input5
[   27.271648] ACPI: Sleep Button (CM) [SBTN]
[   27.375834] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   27.417453] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   27.635887] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.936636] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/LNXVIDEO:00/input/input7
[   27.947595] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.948265] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   27.963569] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   27.963834] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input9
[   27.975574] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   29.000043] Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]
[   29.000067] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.000070] Yenta: Routing CardBus interrupts to PCI
[   29.000075] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   29.232117] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   29.232124] Socket status: 30000020
[   29.232127] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   29.232136] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   29.232140] cs: IO port probe 0xd000-0xefff: clean.
[   29.232894] pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   29.433705] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   29.433745] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   29.895378] pccard: CardBus card inserted into slot 0
[   30.259335] intel8x0_measure_ac97_clock: measured 55232 usecs
[   30.259342] intel8x0: clocking to 48000
[   31.881631] cs: IO port probe 0x100-0x3af: clean.
[   31.882803] cs: IO port probe 0x3e0-0x4ff: clean.
[   31.883322] cs: IO port probe 0x820-0x8ff: clean.
[   31.883381] cs: IO port probe 0xc00-0xcf7: clean.
[   31.883972] cs: IO port probe 0xa00-0xaff: clean.
[   32.806656] loop: module loaded
[   32.858082] lp: driver loaded but no devices found
[   33.104658] Adding 939760k swap on /dev/sda6.  Priority:-1 extents:1 across:939760k
[   33.621651] EXT3 FS on sda5, internal journal
[   33.775753] device-mapper: uevent: version 1.0.3
[   33.775797] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   34.622327] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.238687] No dock devices found.
[   37.969908] apm: BIOS not found.
[   38.298489] ppdev: user-space parallel port driver
[   38.522036] audit(1211461835.808:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5002 profile="/usr/sbin/cupsd" namespace="default"
[   39.934230] [drm] Initialized drm 1.1.0 20060810
[   39.942210] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   39.942224] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.942340] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.883071] Bluetooth: Core ver 2.11
[   41.884448] NET: Registered protocol family 31
[   41.884455] Bluetooth: HCI device and connection manager initialized
[   41.884460] Bluetooth: HCI socket layer initialized
[   41.920167] Bluetooth: L2CAP ver 2.9
[   41.920174] Bluetooth: L2CAP socket layer initialized
[   42.012758] Bluetooth: RFCOMM socket layer initialized
[   42.012786] Bluetooth: RFCOMM TTY layer initialized
[   42.012789] Bluetooth: RFCOMM ver 1.8
[   44.789688] b44: eth0: Link is up at 100 Mbps, full duplex.
[   44.789695] b44: eth0: Flow control is off for TX and off for RX.
[   47.532235] NET: Registered protocol family 17
[   50.604995] NET: Registered protocol family 10
[   50.606113] lo: Disabled Privacy Extensions
[   61.595758] eth0: no IPv6 routers present
stephen@ubuntuinspiron:~/Desktop/i915Graphics/dripkg$ clear
stephen@ubuntuinspiron:~/Desktop/i915Graphics/dripkg$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fec9000 (usable)
[    0.000000]  BIOS-e820: 000000003fec9000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261833) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261833
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261833
[    0.000000] On node 0 totalpages: 261833
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32204 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0
[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3FEF0000, 0028 (r1 DELL    CPi R   27D30A06 ASL        61)
[    0.000000] ACPI: FACP 3FEF0400, 0074 (r1 DELL    CPi R   27D30A06 ASL        61)
[    0.000000] ACPI: DSDT 3FEF0C00, 25D8 (r1 INT430 SYSFexxx     1001 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEFF800, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:beda0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259788
[    0.000000] Kernel command line: root=UUID=3feee4bb-58ca-41da-8a83-8b25f787e2fe ro quiet
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0180f000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2392.370 MHz processor.
[    9.941602] Console: colour VGA+ 80x25
[    9.941608] console [tty0] enabled
[    9.942658] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.943694] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.981552] Memory: 1025832k/1047332k available (2157k kernel code, 20780k reserved, 998k data, 364k init, 129828k highmem)
[    9.981563] virtual kernel memory layout:
[    9.981564]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.981565]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.981566]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.981567]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.981569]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[    9.981570]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[    9.981571]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[    9.981575] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.981651] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.061678] Calibrating delay using timer specific routine.. 4789.18 BogoMIPS (lpj=9578371)
[   10.061731] Security Framework initialized
[   10.061747] SELinux:  Disabled at boot.
[   10.061774] AppArmor: AppArmor initialized
[   10.061780] Failure registering capabilities with primary security module.
[   10.061792] Mount-cache hash table entries: 512
[   10.062034] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   10.062051] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   10.062054] CPU: L2 cache: 512K
[   10.062058] CPU: Hyper-Threading is disabled
[   10.062061] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   10.062079] Compat vDSO mapped to ffffe000.
[   10.062103] Checking 'hlt' instruction... OK.
[   10.078203] SMP alternatives: switching to UP code
[   10.080278] Freeing SMP alternatives: 11k freed
[   10.080449] Early unpacking initramfs... done
[   10.452444] ACPI: Core revision 20070126
[   10.452509] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.453795] ACPI: setting ELCR to 0200 (from 0800)
[   10.454742] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   10.454750] SMP motherboard not detected.
[   10.454753] Local APIC not detected. Using dummy APIC emulation.
[   10.454810] Brought up 1 CPUs
[   10.454833] CPU0 attaching sched-domain:
[   10.454837]  domain 0: span 01
[   10.454839]   groups: 01
[   10.455088] net_namespace: 64 bytes
[   10.455103] Booting paravirtualized kernel on bare hardware
[   10.455799] Time: 14:10:07  Date: 05/22/08
[   10.455835] NET: Registered protocol family 16
[   10.456110] EISA bus registered
[   10.456129] ACPI: bus type pci registered
[   10.509295] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2
[   10.509298] PCI: Using configuration type 1
[   10.509300] Setting up standard PCI resources
[   10.511163] ACPI: EC: Look up EC in DSDT
[   10.514230] ACPI: Interpreter enabled
[   10.514236] ACPI: (supports S0 S1 S3 S4 S5)
[   10.514254] ACPI: Using PIC for interrupt routing
[   10.518947] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.519462] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.519464] * this clock source is slow. If you are sure your timer does not have
[   10.519465] * this bug, please use "acpi_pm_good" to disable the workaround
[   10.519516] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   10.519520] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   10.519828] PCI: Transparent bridge - 0000:00:1e.0
[   10.519907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.520205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   10.527073] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[   10.527183] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[   10.527290] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[   10.527396] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[   10.527491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.527602] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.527748] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.527791] pnp: PnP ACPI init
[   10.527803] ACPI: bus type pnp registered
[   10.537803] pnpacpi: exceeded the max number of IO resources: 40
[   10.537901] pnp: PnP ACPI: found 12 devices
[   10.537905] ACPI: ACPI bus type pnp unregistered
[   10.537911] PnPBIOS: Disabled by ACPI PNP
[   10.538210] PCI: Using ACPI for IRQ routing
[   10.538214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.553668] NET: Registered protocol family 8
[   10.553671] NET: Registered protocol family 20
[   10.553763] AppArmor: AppArmor Filesystem Enabled
[   10.557646] Time: tsc clocksource has been installed.
[   10.565697] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   10.565701] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   10.565704] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[   10.565707] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   10.565710] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved
[   10.565713] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved
[   10.565716] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[   10.565720] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   10.565729] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   10.565732] system 00:02: ioport range 0x800-0x805 has been reserved
[   10.565734] system 00:02: ioport range 0x808-0x80f has been reserved
[   10.565742] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[   10.565745] system 00:03: ioport range 0x806-0x807 has been reserved
[   10.565748] system 00:03: ioport range 0x810-0x85f has been reserved
[   10.565751] system 00:03: ioport range 0x860-0x87f has been reserved
[   10.565753] system 00:03: ioport range 0x880-0x8bf has been reserved
[   10.565756] system 00:03: ioport range 0x8c0-0x8df has been reserved
[   10.565759] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[   10.565769] system 00:08: ioport range 0x900-0x97f has been reserved
[   10.565778] system 00:0b: ioport range 0x7b0-0x7bb has been reserved
[   10.565781] system 00:0b: ioport range 0x7c0-0x7df has been reserved
[   10.565783] system 00:0b: ioport range 0xbb0-0xbbb has been reserved
[   10.565786] system 00:0b: ioport range 0xbc0-0xbdf has been reserved
[   10.565789] system 00:0b: ioport range 0xfb0-0xfbb has been reserved
[   10.565792] system 00:0b: ioport range 0xfc0-0xfdf has been reserved
[   10.565794] system 00:0b: ioport range 0x13b0-0x13bb has been reserved
[   10.565797] system 00:0b: ioport range 0x13c0-0x13df has been reserved
[   10.565800] system 00:0b: ioport range 0x17b0-0x17bb has been reserved
[   10.565803] system 00:0b: ioport range 0x17c0-0x17df has been reserved
[   10.565806] system 00:0b: ioport range 0x1bb0-0x1bbb has been reserved
[   10.565809] system 00:0b: ioport range 0x1bc0-0x1bdf has been reserved
[   10.565811] system 00:0b: ioport range 0x1fb0-0x1fbb has been reserved
[   10.565814] system 00:0b: ioport range 0x1fc0-0x1fdf has been reserved
[   10.565817] system 00:0b: ioport range 0x23b0-0x23bb has been reserved
[   10.565820] system 00:0b: ioport range 0x23c0-0x23df has been reserved
[   10.565822] system 00:0b: ioport range 0x27b0-0x27bb has been reserved
[   10.565825] system 00:0b: ioport range 0x27c0-0x27df has been reserved
[   10.565828] system 00:0b: ioport range 0x2bb0-0x2bbb has been reserved
[   10.565831] system 00:0b: ioport range 0x2bc0-0x2bdf has been reserved
[   10.565834] system 00:0b: ioport range 0x2fb0-0x2fbb has been reserved
[   10.565836] system 00:0b: ioport range 0x2fc0-0x2fdf has been reserved
[   10.565839] system 00:0b: ioport range 0x33b0-0x33bb has been reserved
[   10.565842] system 00:0b: ioport range 0x33c0-0x33df has been reserved
[   10.565845] system 00:0b: ioport range 0x37b0-0x37bb has been reserved
[   10.565848] system 00:0b: ioport range 0x37c0-0x37df has been reserved
[   10.565850] system 00:0b: ioport range 0x3bb0-0x3bbb has been reserved
[   10.565856] system 00:0b: ioport range 0x3bc0-0x3bdf has been reserved
[   10.565859] system 00:0b: ioport range 0x3fb0-0x3fbb has been reserved
[   10.565862] system 00:0b: ioport range 0x3fc0-0x3fdf has been reserved
[   10.565865] system 00:0b: ioport range 0x43b0-0x43bb has been reserved
[   10.565867] system 00:0b: ioport range 0x43c0-0x43df has been reserved
[   10.565870] system 00:0b: ioport range 0x47b0-0x47bb has been reserved
[   10.565873] system 00:0b: ioport range 0x47c0-0x47df has been reserved
[   10.565876] system 00:0b: ioport range 0x4bb0-0x4bbb has been reserved
[   10.565879] system 00:0b: ioport range 0x4bc0-0x4bdf has been reserved
[   10.565882] system 00:0b: ioport range 0x4fb0-0x4fbb has been reserved
[   10.565885] system 00:0b: ioport range 0x4fc0-0x4fdf has been reserved
[   10.565888] system 00:0b: ioport range 0x53b0-0x53bb has been reserved
[   10.565890] system 00:0b: ioport range 0x53c0-0x53df has been reserved
[   10.596439] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   10.596443]   IO window: 0000d000-0000d0ff
[   10.596448]   IO window: 0000d400-0000d4ff
[   10.596453]   PREFETCH window: f8000000-fbffffff
[   10.596458]   MEM window: 54000000-57ffffff
[   10.596462] PCI: Bridge: 0000:00:1e.0
[   10.596466]   IO window: d000-efff
[   10.596472]   MEM window: f8000000-fdffffff
[   10.596476]   PREFETCH window: disabled.
[   10.596493] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.596516] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)
[   10.596707] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   10.596711] PCI: setting IRQ 11 as level-triggered
[   10.596715] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.596738] NET: Registered protocol family 2
[   10.633758] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.634234] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.635629] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.636515] TCP: Hash tables configured (established 131072 bind 65536)
[   10.636521] TCP reno registered
[   10.645933] checking if image is initramfs... it is
[   11.097638] Switched to high resolution mode on CPU 0
[   11.380631] Freeing initrd memory: 7672k freed
[   11.381305] audit: initializing netlink socket (disabled)
[   11.381328] audit(1211465408.400:1): initialized
[   11.381598] highmem bounce pool size: 64 pages
[   11.383927] VFS: Disk quotas dquot_6.5.1
[   11.384031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.384218] io scheduler noop registered
[   11.384220] io scheduler anticipatory registered
[   11.384223] io scheduler deadline registered
[   11.384237] io scheduler cfq registered (default)
[   11.384254] Boot video device is 0000:00:02.0
[   11.384676] isapnp: Scanning for PnP cards...
[   11.737886] isapnp: No Plug & Play device found
[   11.776957] Real Time Clock Driver v1.12ac
[   11.777110] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.778693] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.778783] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.778914] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.779081] i8042.c: Warning: Keylock active.
[   11.781723] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.781730] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.785816] mice: PS/2 mouse device common for all mice
[   11.785980] EISA: Probing bus 0 at eisa.0
[   11.786022] EISA: Detected 0 cards.
[   11.786027] cpuidle: using governor ladder
[   11.786030] cpuidle: using governor menu
[   11.786162] NET: Registered protocol family 1
[   11.786200] Using IPI No-Shortcut mode
[   11.786255] registered taskstats version 1
[   11.786365]   Magic number: 8:746:182
[   11.786415]   hash matches device ttyr8
[   11.786515] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.786518] EDD information not available.
[   11.787067] Freeing unused kernel memory: 364k freed
[   11.789388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.042303] fuse init (API version 7.9)
[   12.072481] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.076559] ACPI: Thermal Zone [THM] (47 C)
[   12.517561] usbcore: registered new interface driver usbfs
[   12.517596] usbcore: registered new interface driver hub
[   12.525521] usbcore: registered new device driver usb
[   12.533529] USB Universal Host Controller Interface driver v3.0
[   12.533626] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.533643] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.533648] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.534049] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.534081] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   12.534269] usb usb1: configuration #1 chosen from 1 choice
[   12.534302] hub 1-0:1.0: USB hub found
[   12.534310] hub 1-0:1.0: 2 ports detected
[   12.637815] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.637822] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.637836] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.637841] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.637871] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.637902] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[   12.638054] usb usb2: configuration #1 chosen from 1 choice
[   12.638084] hub 2-0:1.0: USB hub found
[   12.638092] hub 2-0:1.0: 2 ports detected
[   12.741815] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.741821] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.741838] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.741843] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.741874] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.741904] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   12.742054] usb usb3: configuration #1 chosen from 1 choice
[   12.742084] hub 3-0:1.0: USB hub found
[   12.742092] hub 3-0:1.0: 2 ports detected
[   12.845875] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.845883] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.845900] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.845905] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.845941] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   12.849870] ehci_hcd 0000:00:1d.7: debug port 1
[   12.849878] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   12.849887] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6f7fc00
[   12.865407] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.865574] usb usb4: configuration #1 chosen from 1 choice
[   12.865606] hub 4-0:1.0: USB hub found
[   12.865615] hub 4-0:1.0: 6 ports detected
[   12.869730] SCSI subsystem initialized
[   12.957747] libata version 3.00 loaded.
[   12.971809] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.971825] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.971900] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.971919] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   12.974967] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[   12.974974] PCI: setting IRQ 7 as level-triggered
[   12.974979] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   13.033472] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[   13.033506] b44.c:v2.0
[   13.033540] ata_piix 0000:00:1f.1: version 2.12
[   13.033566] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.033632] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.040803] scsi0 : ata_piix
[   13.049778] scsi1 : ata_piix
[   13.049999] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   13.050003] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   13.053867] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:a8:45:79
[   13.369748] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-4241N, A100, max UDMA/33
[   13.541617] ata1.00: configured for UDMA/33
[   13.705987] ata2.00: ATA-6: FUJITSU MHT2060AH, 006C, max UDMA/100
[   13.705992] ata2.00: 117210240 sectors, multi 8: LBA
[   13.721804] ata2.00: configured for UDMA/100
[   13.727088] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N A100 PQ: 0 ANSI: 5
[   13.727324] scsi 1:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 006C PQ: 0 ANSI: 5
[   13.917384] Driver 'sr' needs updating - please use bus_type methods
[   13.921821] Driver 'sd' needs updating - please use bus_type methods
[   13.938373] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   13.938380] Uniform CD-ROM driver Revision: 3.20
[   13.938459] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   13.938771] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.938789] sd 1:0:0:0: [sda] Write Protect is off
[   13.938792] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.944384] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.944465] sd 1:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.944481] sd 1:0:0:0: [sda] Write Protect is off
[   13.944484] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.944507] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.944511]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   13.946007] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   14.022534]  sda1 sda2 sda3 < sda5 sda6 >
[   14.062047] sd 1:0:0:0: [sda] Attached SCSI disk
[   14.468225] Attempting manual resume
[   14.468231] swsusp: Resume From Partition 8:6
[   14.468233] PM: Checking swsusp image.
[   14.468514] PM: Resume from disk failed.
[   14.487627] EXT3-fs: INFO: recovery required on readonly filesystem.
[   14.487632] EXT3-fs: write access will be enabled during recovery.
[   14.600191] kjournald starting.  Commit interval 5 seconds
[   14.600213] EXT3-fs: recovery complete.
[   14.610092] EXT3-fs: mounted filesystem with ordered data mode.
[   25.900592] Linux agpgart interface v0.102
[   25.940319] agpgart: Detected an Intel 830M Chipset.
[   25.940435] agpgart: Detected 892K stolen memory.
[   25.987849] iTCO_vendor_support: vendor-support=0
[   26.024101] agpgart: AGP aperture is 128M @ 0xe0000000
[   26.024186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   26.028810] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   26.028866] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.071880] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.120625] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.224089] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   26.311787] intel_rng: FWH not detected
[   26.519904] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.971750] ACPI: Battery Slot [BAT0] (battery present)
[   27.239371] ACPI: AC Adapter [AC] (on-line)
[   27.239484] input: Lid Switch as /devices/virtual/input/input3
[   27.242518] ACPI: Lid Switch [LID]
[   27.242575] input: Power Button (CM) as /devices/virtual/input/input4
[   27.255694] ACPI: Power Button (CM) [PBTN]
[   27.255817] input: Sleep Button (CM) as /devices/virtual/input/input5
[   27.271648] ACPI: Sleep Button (CM) [SBTN]
[   27.375834] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   27.417453] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   27.635887] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.936636] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/LNXVIDEO:00/input/input7
[   27.947595] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.948265] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   27.963569] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   27.963834] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input9
[   27.975574] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   29.000043] Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]
[   29.000067] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.000070] Yenta: Routing CardBus interrupts to PCI
[   29.000075] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
[   29.232117] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   29.232124] Socket status: 30000020
[   29.232127] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   29.232136] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   29.232140] cs: IO port probe 0xd000-0xefff: clean.
[   29.232894] pcmcia: parent PCI bridge Memory window: 0xf8000000 - 0xfdffffff
[   29.433705] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   29.433745] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   29.895378] pccard: CardBus card inserted into slot 0
[   30.259335] intel8x0_measure_ac97_clock: measured 55232 usecs
[   30.259342] intel8x0: clocking to 48000
[   31.881631] cs: IO port probe 0x100-0x3af: clean.
[   31.882803] cs: IO port probe 0x3e0-0x4ff: clean.
[   31.883322] cs: IO port probe 0x820-0x8ff: clean.
[   31.883381] cs: IO port probe 0xc00-0xcf7: clean.
[   31.883972] cs: IO port probe 0xa00-0xaff: clean.
[   32.806656] loop: module loaded
[   32.858082] lp: driver loaded but no devices found
[   33.104658] Adding 939760k swap on /dev/sda6.  Priority:-1 extents:1 across:939760k
[   33.621651] EXT3 FS on sda5, internal journal
[   33.775753] device-mapper: uevent: version 1.0.3
[   33.775797] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   34.622327] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.238687] No dock devices found.
[   37.969908] apm: BIOS not found.
[   38.298489] ppdev: user-space parallel port driver
[   38.522036] audit(1211461835.808:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5002 profile="/usr/sbin/cupsd" namespace="default"
[   39.934230] [drm] Initialized drm 1.1.0 20060810
[   39.942210] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   39.942224] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.942340] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.883071] Bluetooth: Core ver 2.11
[   41.884448] NET: Registered protocol family 31
[   41.884455] Bluetooth: HCI device and connection manager initialized
[   41.884460] Bluetooth: HCI socket layer initialized
[   41.920167] Bluetooth: L2CAP ver 2.9
[   41.920174] Bluetooth: L2CAP socket layer initialized
[   42.012758] Bluetooth: RFCOMM socket layer initialized
[   42.012786] Bluetooth: RFCOMM TTY layer initialized
[   42.012789] Bluetooth: RFCOMM ver 1.8
[   44.789688] b44: eth0: Link is up at 100 Mbps, full duplex.
[   44.789695] b44: eth0: Flow control is off for TX and off for RX.
[   47.532235] NET: Registered protocol family 17
[   50.604995] NET: Registered protocol family 10
[   50.606113] lo: Disabled Privacy Extensions
[   61.595758] eth0: no IPv6 routers present
```

---

### Post by Megalorian on 2008-05-22
I don't even want to think about upgrading my bios. It does list the UMA memory as 1MB even though the card actually has 64MB of memory.

I don't think I have compiz running. I'm relatively new to linux and I'm unfamiliar with it, so I could be wrong. Is there are way of verify that it's running? I can't see any compiz related processes running under System Monitor

I don't know anything about DSDT files either, or what XAA mode is.

I can find Xorg.0.log. Where should it be located?

---

### Post by roderick on 2008-05-22
/var/log/Xorg.0.log

I noticed the cipset detected was Intel 830M...

Can you provide also lspci? This will tell me the devices and device ID's of attached hardware (including the video card).

---

### Post by Megalorian on 2008-05-22
Xorg:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux ubuntuinspiron 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 22 14:10:35 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1028,0149 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,24c0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,24c0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,24c0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0149 rev 02 class 04,01,00 hdr 00
(II) PCI: 02:01:0: chip 14e4,4401 card 4401,1028 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 104c,ac56 card d000,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 03:00:0: chip 10ec,8185 card 10ec,8185 rev 20 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[4] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfdffffff (0x6000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xe0000000/27, 0xf6f80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[1] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[2] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[11] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[12] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[13] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[16] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[17] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[1] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[1] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[2] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[9] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[10] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[11] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[12] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[13] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[16] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[17] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[1] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[5] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[6] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[23] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[24] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 845G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[5] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[6] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[23] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[24] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[5] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[6] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[26] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF6F80000
(II) intel(0): 1 display pipe available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C device "DVOI2C_E:CH7017/7018/7019 LVDS Controller" registered at address 0xEA.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf6f80000 - 0xf6ffffff (0x80000) MS[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfcffe000 - 0xfcffffff (0x2000) MX[B]
	[7] -1	0	0xf6f7f400 - 0xf6f7f4ff (0x100) MX[B]
	[8] -1	0	0xf6f7f800 - 0xf6f7f9ff (0x200) MX[B]
	[9] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[10] -1	0	0xf6f7fc00 - 0xf6f7ffff (0x400) MX[B]
	[11] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[12] -1	0	0xf6f80000 - 0xf6ffffff (0x80000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0x54000000 - 0x540003ff (0x400) MX[B]
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000cc40 - 0x0000cc7f (0x40) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 240640 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 962556 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xf6f80000
(II) intel(0): [drm] ring buffer = 0xe0000000
(II) intel(0): [drm] mapped front buffer at 0xe0400000, handle = 0xe0400000
(II) intel(0): [drm] mapped back buffer at 0xe1400000, handle = 0xe1400000
(II) intel(0): [drm] mapped depth buffer at 0xe1800000, handle = 0xe1800000
(II) intel(0): [drm] mapped classic textures at 0xe1c00000, handle = 0xe1c00000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xe0000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 12582912 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x000df000 (pgoffset 223)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00400000 (pgoffset 1024)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01400000 (pgoffset 5120)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x01c00000 (pgoffset 7168)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB)
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB)
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x000dffff: overlay registers (4 kB, 0x00000000374e7000 physical
)
(II) intel(0): 0x00400000-0x007fffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00800000-0x013fffff: exa offscreen (12288 kB)
(II) intel(0): 0x01400000-0x017fffff: back buffer (4096 kB) X tiled
(II) intel(0): 0x01800000-0x01bfffff: depth buffer (4096 kB) X tiled
(II) intel(0): 0x01c00000-0x03bfffff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Registers before mode setting
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_INPUT: 00
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_OUTPUT: 00
(II) intel(0): CH7017_VERTICAL_ACTIVE_LINE_OUTPUT: 00
(II) intel(0): CH7017_ACTIVE_INPUT_LINE_OUTPUT: 1a
(II) intel(0): CH7017_LVDS_PLL_VCO_CONTROL: ad
(II) intel(0): CH7017_LVDS_PLL_FEEDBACK_DIV: ad
(II) intel(0): CH7017_LVDS_CONTROL_2: 80
(II) intel(0): CH7017_OUTPUTS_ENABLE: c8
(II) intel(0): CH7017_LVDS_POWER_DOWN: 53
(II) intel(0): Registers after mode setting
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_INPUT: 00
(II) intel(0): CH7017_HORIZONTAL_ACTIVE_PIXEL_OUTPUT: 00
(II) intel(0): CH7017_VERTICAL_ACTIVE_LINE_OUTPUT: 00
(II) intel(0): CH7017_ACTIVE_INPUT_LINE_OUTPUT: 1c
(II) intel(0): CH7017_LVDS_PLL_VCO_CONTROL: a3
(II) intel(0): CH7017_LVDS_PLL_FEEDBACK_DIV: ad
(II) intel(0): CH7017_LVDS_CONTROL_2: 20
(II) intel(0): CH7017_OUTPUTS_ENABLE: 08
(II) intel(0): CH7017_LVDS_POWER_DOWN: 0c
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 11
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(WW) intel(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ie"
(**) Generic Keyboard: XkbLayout: "ie"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.
(II) intel(0): I2C device "DVODDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "DVODDC_D:ddc2" removed.

```

---

### Post by Megalorian on 2008-05-22
LSPCI:
```


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```

---

### Post by roderick on 2008-05-22
Ok, so you have an Intel 845GME. It looks like the Xorg log file does not detect any valid display modes.

Can you add an attachment of the Xorg.0.log file you just posted and can you get a copy of the same log file when the display does work (as you indicated it sometimes does) and add as an attachment (rather than paste). I need to diff the files to see if there are any significant differences.

Second, I want you to try forcing XAA rather than EXA, to see if it's related to that (though I think it's not). To change this, you need to modify the Device section in your /etc/X11/xorg.conf and add an option line. Look for the section below and add the 'Option "AccelMethod" "XAA"' line

```

Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "XAA"
EndSection

```

This may or may not help.

---

### Post by Megalorian on 2008-05-22
Here are the log files

---

### Post by Megalorian on 2008-05-22
> Second, I want you to try forcing XAA rather than EXA, to see if it's related to that (though I think it's not). To change this, you need to modify the Device section in your /etc/X11/xorg.conf and add an option line. Look for the section below and add the 'Option "AccelMethod" "XAA"' line

Code:

Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "XAA"
EndSection

This may or may not help.

I tried this and it didn't work unfortunately.

---

### Post by roderick on 2008-05-22
Can you try adding 'apic lapic' to your kernel command line?

I noticed in your dmesg that it was disabled, and this may be part of the problem experienced later on.

Another possible option for the kernel, may be usb-handoff (don't test that until you've tested the apic one above first).

These may not correct, but worth a shot.

I believe input6 and input9 are trashing one another (input6 is touchpad and input9 is video). In the non-working log, event9 (which normally matches input9) is instead assigned to the touchpad. Maybe there is some detection broken that is confusing the two.

Not sure.

---

### Post by Megalorian on 2008-05-22
How do I add 'apic lapic' to the kernel command line (just bear in mind that I'm still new to Linux)?

I'll be away from my computer for the next 2 hours, so I'll try this later on.

Thanks for all your help so far.

---

### Post by roderick on 2008-05-22
To add this, you need to edit the menu.lst file used by grub (the bootloader).

/boot/grub/menu.lst

In this file, look for the line: ## ## End Default Options ##

Look for the line starting with kernel just below this. place the apic lapic at the end of that line.

---

### Post by Megalorian on 2008-05-22
I've added apic lapic to the kernel line

kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=3feee4bb-58ca-41da-8a83-8b25f787e2fe ro quiet apic lapic

Still no dice. I had the usual problem where I get the black screen and had to reboot 2/3 times until I got a login screen. Strange.

---

### Post by roderick on 2008-05-22
can you provide the latest dmesg so I can see what is happening with the lapic enabled? Just to see if there is any difference.

Other than this, it looks like it is a bug with evdev (event subsystem) - potentially. Can you try a few times and confirm if event6 and event9 change and under which circumstances it works? 

Earlier I mentioned:

"I believe input6 and input9 are trashing one another (input6 is touchpad and input9 is video). In the non-working log, event9 (which normally matches input9) is instead assigned to the touchpad. Maybe there is some detection broken that is confusing the two."

So, basically, what I would like to confirm is if event6 is always the touchpad when things work and event9 when it fails. That could be a hint that the auto-detection is not working correctly and that's something you can post to both launchpad and freedesktop.org bug lists. The package is either xserver-xorg-input-evdev or the kernel module evdev and the problem is touchpad and video events not assigned correctly (one trashes the other).

At least that's what it appears to be, as your Xorg.0.log doesn't give any additional info to detect beyond that.

Not sure if we can force the order of detection... force the touchpad to get picked up first to ensure it get event6/input6... 

Maybe the evdev kernel module is not getting loaded properly during boot. Can you add it to your /etc/modules (add a new line with evdev on it). Reboot.

Anyway, test and let me know. You got me stumped... but still very curious :)

---

### Post by Megalorian on 2008-05-22
Here is the latest dmesg from my last successful login

I'm not sure how to obtain a dmesg if I can't succefully login. I think you can do a CNTL - ALT F2/F1, but that didn't work when the screen turned blank 

Here is the 'input' lines from my last 3 successfull logins as well. It looks like what you say it should be:

Sucessfull login

[   12.038110] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.054704] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   27.161109] input: Lid Switch as /devices/virtual/input/input2
[   27.161501] input: Power Button (CM) as /devices/virtual/input/input3
[   27.176947] input: Sleep Button (CM) as /devices/virtual/input/input4
[   27.306989] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/LNXVIDEO:00/input/input5
[   27.321392] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   27.337018] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   29.038851] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   29.758365] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

Sucessfull login

[   11.973842] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.981219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.887212] input: Lid Switch as /devices/virtual/input/input2
[   26.887588] input: Power Button (CM) as /devices/virtual/input/input3
[   26.899129] input: Sleep Button (CM) as /devices/virtual/input/input4
[   27.225103] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/LNXVIDEO:00/input/input5
[   27.239548] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   27.251115] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   28.871418] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   29.579046] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

Sucessfull login

[   12.492122] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.499944] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.913915] input: Lid Switch as /devices/virtual/input/input2
[   26.914294] input: Power Button (CM) as /devices/virtual/input/input3
[   26.925780] input: Sleep Button (CM) as /devices/virtual/input/input4
[   27.270134] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/LNXVIDEO:00/input/input5
[   27.282305] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   27.297902] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   28.754497] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   29.555597] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

---

### Post by Megalorian on 2008-05-22
I added 'evdev' to the modules file as follows. Does the seqence matter? I just added it at the beginning. I will be testing it shortly.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

evdev
loop
lp
fuse

---

### Post by Megalorian on 2008-05-22
It failed again resulting in another blank screen. This time, i was able to drop into cmdline mode. So here is the dmseg file

---

