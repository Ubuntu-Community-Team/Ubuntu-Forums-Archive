---
title: "intelfb doesn't work during boot time, or when I boot without window manager"
date: 2008-11-20
forum: Multimedia Software
---

### Post by sternocera on 2008-11-20
Hello,

I'm attempting to build a Xubuntu powered embedded system. XFCE itself is only used for maintenance. Software that writes directly to the framebuffer figures prominently in this embedded system. The hardware I'm using uses the intelfb kernel module. I got the module working by appending "video=intelfb vga=788" to my kernel's entry in "/boot/grub/menu.lst". 

The intelfb kernel module has an odd side-effect: During boot, dmesg output and/or the splashscreen aren't visible: All that is visible is a still white underscore in the top left hand corner, no matter what I do.

When my window manager starts, it, and everything else, works fine. I can now change virtual terminals in the usual way (ctrl, alt + F1, etc), and see a high resolution terminal that uses the framebuffer. 

The big problem occurs when I stop XFCE starting at boot time:

sudo update-rc.d -f gdm remove

Now, the system never gets past just displaying the white underscore. 

I suspect this has something to do with the kernel message "intelfb: Cannot reserve FB region". I've included my dmesg in its entirety.

Any help you can give is *hugely* appreciated, because I'm at my wit's end on this one!

Thanks,
Sternocera

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000dff0000 (usable)
[    0.000000]  BIOS-e820: 000000000dff0000 - 000000000dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000dff3000 - 000000000e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 223MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 57328) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    57328
[    0.000000]   HighMem     57328 ->    57328
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    57328
[    0.000000] On node 0 totalpages: 57328
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 415 pages used for memmap
[    0.000000]   Normal zone: 52817 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6840 checksum 0
[    0.000000] ACPI: RSDP 000F6840, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 0DFF3040, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 0DFF30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 0DFF3180, 3FC5 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 0DFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f0c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56881
[    0.000000] Kernel command line: root=UUID=0c8c48a7-334b-4698-a8d1-df5fdce8283d ro quiet splash 8250.nr_uarts=6 video=intelfb vga=788
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1196.156 MHz processor.
[   15.554795] Console: colour dummy device 80x25
[   15.554803] console [tty0] enabled
[   15.554990] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.555188] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.564687] Memory: 215300k/229312k available (2177k kernel code, 13452k reserved, 1006k data, 368k init, 0k highmem)
[   15.564705] virtual kernel memory layout:
[   15.564707]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.564710]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.564712]     vmalloc : 0xce800000 - 0xff7fe000   ( 783 MB)
[   15.564714]     lowmem  : 0xc0000000 - 0xcdff0000   ( 223 MB)
[   15.564717]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   15.564719]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   15.564721]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   15.564728] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.564791] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.644821] Calibrating delay using timer specific routine.. 2396.12 BogoMIPS (lpj=4792254)
[   15.644870] Security Framework initialized
[   15.644883] SELinux:  Disabled at boot.
[   15.644911] AppArmor: AppArmor initialized
[   15.644922] Failure registering capabilities with primary security module.
[   15.644940] Mount-cache hash table entries: 512
[   15.645192] Initializing cgroup subsys ns
[   15.645201] Initializing cgroup subsys cpuacct
[   15.645224] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   15.645252] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   15.645259] CPU: L2 cache: 256K
[   15.645264] CPU: Hyper-Threading is disabled
[   15.645269] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   15.645296] Compat vDSO mapped to ffffe000.
[   15.645323] Checking 'hlt' instruction... OK.
[   15.661545] SMP alternatives: switching to UP code
[   15.664697] Freeing SMP alternatives: 11k freed
[   15.664987] Early unpacking initramfs... done
[   16.363242] ACPI: Core revision 20070126
[   16.363363] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.367084] ACPI: setting ELCR to 0200 (from 1a60)
[   16.548818] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 1.20GHz stepping 09
[   16.548834] SMP motherboard not detected.
[   16.656866] Brought up 1 CPUs
[   16.656897] CPU0 attaching sched-domain:
[   16.656904]  domain 0: span 01
[   16.656909]   groups: 01
[   16.657324] net_namespace: 64 bytes
[   16.657336] Booting paravirtualized kernel on bare hardware
[   16.658551] Time: 14:43:11  Date: 11/20/08
[   16.658605] NET: Registered protocol family 16
[   16.659179] EISA bus registered
[   16.659221] ACPI: bus type pci registered
[   16.684072] PCI: PCI BIOS revision 2.10 entry at 0xfa9f0, last bus=1
[   16.684078] PCI: Using configuration type 1
[   16.684087] Setting up standard PCI resources
[   16.717665] ACPI: EC: Look up EC in DSDT
[   16.725974] ACPI: Interpreter enabled
[   16.725984] ACPI: (supports S0 S1 S4 S5)
[   16.726020] ACPI: Using PIC for interrupt routing
[   16.739024] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.739917] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   16.739921] * this clock source is slow. If you are sure your timer does not have
[   16.739923] * this bug, please use "acpi_pm_good" to disable the workaround
[   16.739993] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   16.740000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   16.740483] PCI: Transparent bridge - 0000:00:1e.0
[   16.740530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.741054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.756065] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.756298] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   16.756524] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.756747] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   16.756991] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.757219] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.757446] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.757671] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.758013] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.758104] pnp: PnP ACPI init
[   16.758125] ACPI: bus type pnp registered
[   16.767795] pnp: PnP ACPI: found 17 devices
[   16.767803] ACPI: ACPI bus type pnp unregistered
[   16.767813] PnPBIOS: Disabled by ACPI PNP
[   16.768494] PCI: Using ACPI for IRQ routing
[   16.768502] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.796789] NET: Registered protocol family 8
[   16.796795] NET: Registered protocol family 20
[   16.796972] AppArmor: AppArmor Filesystem Enabled
[   16.800765] Time: tsc clocksource has been installed.
[   16.808886] system 00:01: ioport range 0xb78-0xb7b has been reserved
[   16.808894] system 00:01: ioport range 0xf78-0xf7b has been reserved
[   16.808900] system 00:01: ioport range 0xa78-0xa7b has been reserved
[   16.808905] system 00:01: ioport range 0xe78-0xe7b has been reserved
[   16.808911] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[   16.808916] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[   16.808922] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   16.808927] system 00:01: ioport range 0x294-0x297 has been reserved
[   16.808957] system 00:0e: ioport range 0x400-0x4bf could not be reserved
[   16.808976] system 00:10: iomem range 0xd0000-0xd3fff has been reserved
[   16.808983] system 00:10: iomem range 0xdd400-0xdffff has been reserved
[   16.808989] system 00:10: iomem range 0xf0000-0xfbfff could not be reserved
[   16.808995] system 00:10: iomem range 0xfc000-0xfffff could not be reserved
[   16.809002] system 00:10: iomem range 0xdff0000-0xdffffff could not be reserved
[   16.809008] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[   16.809014] system 00:10: iomem range 0x100000-0xdfeffff could not be reserved
[   16.809021] system 00:10: iomem range 0xfec00000-0xfecfffff could not be reserved
[   16.809027] system 00:10: iomem range 0xfee00000-0xfeefffff could not be reserved
[   16.809033] system 00:10: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   16.809040] system 00:10: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.809046] system 00:10: iomem range 0xe0000-0xeffff has been reserved
[   16.840239] PCI: Bridge: 0000:00:1e.0
[   16.840248]   IO window: d000-dfff
[   16.840257]   MEM window: e8000000-e80fffff
[   16.840265]   PREFETCH window: disabled.
[   16.840287] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.840315] NET: Registered protocol family 2
[   16.876921] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   16.877457] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   16.877529] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.877598] TCP: Hash tables configured (established 8192 bind 8192)
[   16.877603] TCP reno registered
[   16.889047] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.546094]  it is
[   18.259805] Freeing initrd memory: 7316k freed
[   18.261072] audit: initializing netlink socket (disabled)
[   18.261098] audit(1227192192.416:1): initialized
[   18.266394] VFS: Disk quotas dquot_6.5.1
[   18.266601] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.266929] io scheduler noop registered
[   18.266935] io scheduler anticipatory registered
[   18.266939] io scheduler deadline registered
[   18.266973] io scheduler cfq registered (default)


[   18.267000] Boot video device is 0000:00:02.0
[   18.267797] isapnp: Scanning for PnP cards...
[   18.622585] isapnp: No Plug & Play device found
[   18.735231] Real Time Clock Driver v1.12ac
[   18.735469] Serial: 8250/16550 driver $Revision: 1.90 $ 6 ports, IRQ sharing enabled
[   18.735679] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.736012] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.736304] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   18.736625] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   18.738206] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.738981] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.739872] 00:0a: ttyS2 at I/O 0x3e8 (irq = 10) is a 16550A
[   18.740676] 00:0b: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
[   18.741464] 00:0c: ttyS4 at I/O 0x4f8 (irq = 10) is a 16550A
[   18.742260] 00:0d: ttyS5 at I/O 0x4e8 (irq = 10) is a 16550A
[   18.744362] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.744619] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.744895] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   18.744901] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   18.745406] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.752797] mice: PS/2 mouse device common for all mice
[   18.753136] EISA: Probing bus 0 at eisa.0
[   18.753189] EISA: Detected 0 cards.
[   18.753194] cpuidle: using governor ladder
[   18.753199] cpuidle: using governor menu
[   18.753393] NET: Registered protocol family 1
[   18.753458] Using IPI No-Shortcut mode
[   18.753525] registered taskstats version 1
[   18.753714]   Magic number: 0:702:738
[   18.753908] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.753912] EDD information not available.
[   18.754410] Freeing unused kernel memory: 368k freed
[   18.788556] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.972604] vesafb: framebuffer at 0xd8000000, mapped to 0xce880000, using 1875k, total 32576k
[   18.972614] vesafb: mode is 800x600x16, linelength=1600, pages=32
[   18.972619] vesafb: scrolling: redraw
[   18.972625] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   18.972917] Console: switching to colour frame buffer device 100x37
[   19.000045] fb0: VESA VGA frame buffer device
[   20.329801] fuse init (API version 7.9)
[   20.363479] ACPI: Fan [FAN] (on)
[   20.376849] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   20.376864] ACPI: Processor [CPU0] (supports 2 throttling states)
[   20.376903] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.412490] ACPI: Thermal Zone [THRM] (26 C)
[   21.912145] usbcore: registered new interface driver usbfs
[   21.912202] usbcore: registered new interface driver hub
[   21.941681] usbcore: registered new device driver usb
[   22.059325] SCSI subsystem initialized
[   22.080063] USB Universal Host Controller Interface driver v3.0
[   22.080533] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   22.080542] PCI: setting IRQ 11 as level-triggered
[   22.080548] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.080569] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.080576] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.081091] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.081137] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000e000
[   22.081448] usb usb1: configuration #1 chosen from 1 choice
[   22.081503] hub 1-0:1.0: USB hub found
[   22.081518] hub 1-0:1.0: 2 ports detected
[   22.184557] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[   22.184567] PCI: setting IRQ 6 as level-triggered
[   22.184573] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[   22.184595] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.184603] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.184677] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.184714] uhci_hcd 0000:00:1d.1: irq 6, io base 0x0000e100
[   22.184984] usb usb2: configuration #1 chosen from 1 choice
[   22.185041] hub 2-0:1.0: USB hub found
[   22.185055] hub 2-0:1.0: 2 ports detected
[   22.236032] 8139too Fast Ethernet driver 0.9.28
[   22.249791] libata version 3.00 loaded.
[   22.288547] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   22.288557] PCI: setting IRQ 9 as level-triggered
[   22.288564] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   22.288585] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.288593] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.288659] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.288694] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000e200
[   22.288956] usb usb3: configuration #1 chosen from 1 choice
[   22.289013] hub 3-0:1.0: USB hub found
[   22.289027] hub 3-0:1.0: 2 ports detected
[   22.392773] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   22.392783] PCI: setting IRQ 5 as level-triggered
[   22.392790] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   22.392813] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.392821] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.392903] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.396844] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.396862] ehci_hcd 0000:00:1d.7: irq 5, io mem 0xe8200000
[   22.424035] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   22.436019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.436292] usb usb4: configuration #1 chosen from 1 choice
[   22.436352] hub 4-0:1.0: USB hub found
[   22.436368] hub 4-0:1.0: 6 ports detected
[   22.540420] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.541442] eth0: RealTek RTL8139 at 0xd000, 00:60:ef:05:b5:f2, IRQ 11
[   22.541450] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   22.547838] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   22.547965] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.547996] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   22.559976] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.594312] ata_piix 0000:00:1f.1: version 2.12
[   22.594350] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   22.594430] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.604002] scsi0 : ata_piix
[   22.617116] scsi1 : ata_piix
[   22.618351] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   22.618359] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   22.828619] ata1.00: ATA-7: ST380215A, 3.AAC, max UDMA/100
[   22.828628] ata1.00: 156301488 sectors, multi 16: LBA48 
[   22.895230] ata1.00: configured for UDMA/100
[   22.963943] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   23.048193] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[   23.147141] usb 1-1: configuration #1 chosen from 1 choice
[   23.887894] Driver 'sd' needs updating - please use bus_type methods
[   23.888076] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.888110] sd 0:0:0:0: [sda] Write Protect is off
[   23.888117] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.888168] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.888290] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.888320] sd 0:0:0:0: [sda] Write Protect is off
[   23.888326] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.888375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.888384]  sda: sda1 sda2 <<6>usbcore: registered new interface driver hiddev
[   23.937934]  sda5 >
[   23.938163] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.949550] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   23.952732] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.963890] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[   23.963931] usbcore: registered new interface driver usbhid
[   23.963940] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.502502] Attempting manual resume
[   24.502511] swsusp: Resume From Partition 8:5
[   24.502515] PM: Checking swsusp image.
[   24.502768] PM: Resume from disk failed.
[   24.580590] kjournald starting.  Commit interval 5 seconds
[   24.580619] EXT3-fs: mounted filesystem with ordered data mode.
[   34.438257] Linux agpgart interface v0.102
[   34.610382] agpgart: Detected an Intel 855GM Chipset.
[   34.610558] agpgart: Detected 32636K stolen memory.
[   34.620967] agpgart: AGP aperture is 128M @ 0xd8000000
[   34.866200] intelfb: Framebuffer driver for Intel(R) 830M/845G/852GM/855GM/865G/915G/915GM/945G/945GM chipsets
[   34.866210] intelfb: Version 0.9.4
[   34.866449] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.866465] intelfb: Cannot reserve FB region.
[   35.098233] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.190113] intel_rng: FWH not detected
[   35.238354] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.386134] iTCO_vendor_support: vendor-support=0
[   35.442110] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.442388] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   35.442494] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.759855] input: Power Button (FF) as /devices/virtual/input/input3
[   35.770047] ACPI: Power Button (FF) [PWRF]
[   35.770291] input: Power Button (CM) as /devices/virtual/input/input4
[   35.786006] ACPI: Power Button (CM) [PWRB]
[   36.742230] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   40.271522] parport_pc 00:08: reported by Plug and Play ACPI
[   40.271584] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.990239] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   40.990251] PCI: setting IRQ 12 as level-triggered
[   40.990257] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   40.990301] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.313218] intel8x0_measure_ac97_clock: measured 54984 usecs
[   41.313226] intel8x0: clocking to 48000
[   44.109014] loop: module loaded
[   44.142533] lp0: using parport0 (interrupt-driven).
[   44.281454] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
[   44.722092] EXT3 FS on sda1, internal journal
[   45.778676] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.739545] No dock devices found.
[   53.314736] NET: Registered protocol family 10
[   53.315899] lo: Disabled Privacy Extensions
[   55.541422] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   55.541433] apm: overridden by ACPI.
[   55.701041] ppdev: user-space parallel port driver
[   55.867395] audit(1227192230.919:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4747 profile="/usr/sbin/cupsd" namespace="default"
[   57.995479] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.318793] Bluetooth: Core ver 2.11
[   58.327142] NET: Registered protocol family 31
[   58.327152] Bluetooth: HCI device and connection manager initialized
[   58.327161] Bluetooth: HCI socket layer initialized
[   58.377392] Bluetooth: L2CAP ver 2.9
[   58.377402] Bluetooth: L2CAP socket layer initialized
[   58.475669] Bluetooth: RFCOMM socket layer initialized
[   58.476188] Bluetooth: RFCOMM TTY layer initialized
[   58.476198] Bluetooth: RFCOMM ver 1.8
[   59.004345] [drm] Initialized drm 1.1.0 20060810
[   59.013728] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.014426] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.014965] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   59.015110] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   59.656122] serio: Serial port ttyS4
[   59.802532] elo: AccuTouch touchscreen, fw: 02.01, features: 002x, controller: 0x0e
[   59.802677] input: Elo Serial TouchScreen as /devices/serio1/input/input6
[   61.292125] NET: Registered protocol family 17
[   73.177020] eth0: no IPv6 routers present

```

---

