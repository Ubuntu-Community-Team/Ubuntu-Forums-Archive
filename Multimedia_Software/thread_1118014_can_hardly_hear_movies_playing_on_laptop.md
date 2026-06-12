---
title: "can hardly hear movies playing on laptop"
date: 2009-04-06
forum: Multimedia Software
---

### Post by Prium on 2009-04-06
I know the speakers are capable of producing more db than what I am currently getting 'maxed out' in ubuntu with mplayer, because they are so much louder in windows when I play DVDs.

I have read about the same problem here in more than one thread and have tried using alsamixer and the softvol-max thing with mplayer, but alsamixer does nothing beyond what the volume buttons do, and the extra command with mplayer makes no differnce to the volume at all. 

Is there anything else I should try?

---

### Post by khelben1979 on 2009-04-06
I suspect that the sound will never get up as high as what you can get with a Windows system, but... maybe your sound drivers isn't the best for your computer hardware?

What soundcard/soundchip do you have over there? ```
sudo dmesg
``` will show what you got inside.

---

### Post by Prium on 2009-04-07
This is what it lists, but it is truncated for some reason. Why does everything in Linux have to be so awkward!



[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127651
[    0.000000] Kernel command line: root=UUID=93e14706-df8b-48d0-9b9f-2ee70c4ac711 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1733.433 MHz processor.
[   10.326844] Console: colour VGA+ 80x25
[   10.326848] console [tty0] enabled
[   10.327001] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.327197] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.337573] Memory: 498040k/514624k available (2179k kernel code, 15896k reserved, 1008k data, 368k init, 0k highmem)
[   10.337581] virtual kernel memory layout:
[   10.337582]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   10.337583]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.337585]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   10.337586]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   10.337587]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   10.337588]       .data : 0xc0320c08 - 0xc041cdc4   (1008 kB)
[   10.337590]       .text : 0xc0100000 - 0xc0320c08   (2179 kB)
[   10.337593] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.337631] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.337777] hpet clockevent registered
[   10.417682] Calibrating delay using timer specific routine.. 3470.82 BogoMIPS (lpj=6941653)
[   10.417706] Security Framework initialized
[   10.417714] SELinux:  Disabled at boot.
[   10.417727] AppArmor: AppArmor initialized
[   10.417731] Failure registering capabilities with primary security module.
[   10.417740] Mount-cache hash table entries: 512
[   10.417860] Initializing cgroup subsys ns
[   10.417865] Initializing cgroup subsys cpuacct
[   10.417875] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000 00000000
[   10.417883] monitor/mwait feature present.
[   10.417885] using mwait in idle threads.
[   10.417889] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.417892] CPU: L2 cache: 1024K
[   10.417896] CPU: After all inits, caps: afe9fbff 00100000 00000000 00042940 0000c109 00000000 00000000 00000000
[   10.417905] Compat vDSO mapped to ffffe000.
[   10.417918] Checking 'hlt' instruction... OK.
[   10.434091] SMP alternatives: switching to UP code
[   10.435909] Freeing SMP alternatives: 11k freed
[   10.436022] Early unpacking initramfs... done
[   10.787817] ACPI: Core revision 20070126
[   10.787899] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.792357] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[   10.792377] Total of 1 processors activated (3470.82 BogoMIPS).
[   10.792573] ENABLING IO-APIC IRQs
[   10.792768] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.937065] Brought up 1 CPUs
[   10.937091] CPU0 attaching sched-domain:
[   10.937094]  domain 0: span 01
[   10.937096]   groups: 01
[   10.937267] net_namespace: 64 bytes
[   10.937276] Booting paravirtualized kernel on bare hardware
[   10.937735] Time:  7:56:01  Date: 04/07/09
[   10.937760] NET: Registered protocol family 16
[   10.937960] EISA bus registered
[   10.937965] ACPI: bus type pci registered
[   10.965440] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12
[   10.965443] PCI: Using configuration type 1
[   10.965453] Setting up standard PCI resources
[   10.967357] ACPI: EC: Look up EC in DSDT
[   10.969488] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   10.969491] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   11.568304] ACPI: Interpreter enabled
[   11.568307] ACPI: (supports S0 S3 S4 S5)
[   11.568320] ACPI: Using IOAPIC for interrupt routing
[   11.605518] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   11.605521] ACPI: EC: driver started in poll mode
[   11.605562] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.606378] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.606383] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   11.607199] PCI: Transparent bridge - 0000:00:1e.0
[   11.607289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.607610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.607746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.607878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   11.608024] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.612632] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   11.612742] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.612848] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.612953] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   11.613059] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.613164] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.613269] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.613374] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.613507] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.613539] pnp: PnP ACPI init
[   11.613547] ACPI: bus type pnp registered
[   11.616318] pnp: PnP ACPI: found 9 devices
[   11.616321] ACPI: ACPI bus type pnp unregistered
[   11.616325] PnPBIOS: Disabled by ACPI PNP
[   11.616598] PCI: Using ACPI for IRQ routing
[   11.616601] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.616605] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   11.616607] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   11.616610] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   11.616612] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   11.616614] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   11.616617] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   11.616619] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   11.616621] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   11.616624] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   11.660103] NET: Registered protocol family 8
[   11.660105] NET: Registered protocol family 20
[   11.660140] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.660145] hpet0: 3 64-bit timers, 14318180 Hz
[   11.661192] AppArmor: AppArmor Filesystem Enabled
[   11.664091] Time: tsc clocksource has been installed.
[   11.664107] Switched to high resolution mode on CPU 0
[   11.672049] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.672052] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   11.672055] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   11.672059] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   11.672062] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   11.672065] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   11.672068] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   11.672071] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   11.672078] system 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved
[   11.672084] system 00:05: ioport range 0x800-0x80f has been reserved
[   11.672087] system 00:05: ioport range 0x1000-0x107f has been reserved
[   11.672090] system 00:05: ioport range 0x1180-0x11bf has been reserved
[   11.672093] system 00:05: ioport range 0x1600-0x166f has been reserved
[   11.672096] system 00:05: ioport range 0xfe10-0xfe11 has been reserved
[   11.672099] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[   11.702515] PCI: Bridge: 0000:00:1c.0
[   11.702519]   IO window: 2000-2fff
[   11.702525]   MEM window: 30000000-300fffff
[   11.702529]   PREFETCH window: disabled.
[   11.702535] PCI: Bridge: 0000:00:1c.1
[   11.702537]   IO window: disabled.
[   11.702542]   MEM window: disabled.
[   11.702546]   PREFETCH window: disabled.
[   11.702552] PCI: Bridge: 0000:00:1c.2
[   11.702553]   IO window: disabled.
[   11.702560]   MEM window: disabled.
[   11.702564]   PREFETCH window: disabled.
[   11.702573] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[   11.702575]   IO window: 00001400-000014ff
[   11.702580]   IO window: 00001c00-00001cff
[   11.702585]   PREFETCH window: 34000000-37ffffff
[   11.702590]   MEM window: 38000000-3bffffff
[   11.702595] PCI: Bridge: 0000:00:1e.0
[   11.702597]   IO window: disabled.
[   11.702602]   MEM window: d0100000-d01fffff
[   11.702607]   PREFETCH window: disabled.
[   11.702638] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   11.702646] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.702654] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.702679] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   11.702686] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.702710] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.702717] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.702728] PCI: Enabling device 0000:00:1e.0 (0004 -> 0006)
[   11.702735] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.702751] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003)
[   11.702755] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   11.702774] NET: Registered protocol family 2
[   11.739990] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   11.740175] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   11.740276] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   11.740374] TCP: Hash tables configured (established 16384 bind 16384)
[   11.740377] TCP reno registered
[   11.752040] checking if image is initramfs... it is
[   12.442031] Freeing initrd memory: 7315k freed
[   12.442230] Simple Boot Flag at 0x36 set to 0x1
[   12.442757] audit: initializing netlink socket (disabled)
[   12.442774] audit(1239090961.996:1): initialized
[   12.444828] VFS: Disk quotas dquot_6.5.1
[   12.444899] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.445045] io scheduler noop registered
[   12.445048] io scheduler anticipatory registered
[   12.445050] io scheduler deadline registered
[   12.445061] io scheduler cfq registered (default)
[   12.445074] Boot video device is 0000:00:02.0
[   12.445280] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.445338] assign_interrupt_mode Found MSI capability
[   12.445387] Allocate Port Service[0000:00:1c.0:pcie00]
[   12.445424] Allocate Port Service[0000:00:1c.0:pcie02]
[   12.445526] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.445583] assign_interrupt_mode Found MSI capability
[   12.445628] Allocate Port Service[0000:00:1c.1:pcie00]
[   12.445661] Allocate Port Service[0000:00:1c.1:pcie02]
[   12.445762] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.445819] assign_interrupt_mode Found MSI capability
[   12.445864] Allocate Port Service[0000:00:1c.2:pcie00]
[   12.445897] Allocate Port Service[0000:00:1c.2:pcie02]
[   12.446160] isapnp: Scanning for PnP cards...
[   12.800013] isapnp: No Plug & Play device found
[   12.828355] Real Time Clock Driver v1.12ac
[   12.828598] hpet_resources: 0xfed00000 is busy
[   12.828630] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.829838] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.829907] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.830001] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.845395] i8042.c: Detected active multiplexing controller, rev 1.1.
[   12.851317] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.851322] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   12.851324] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   12.851327] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   12.851329] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   12.862554] mice: PS/2 mouse device common for all mice
[   12.862669] EISA: Probing bus 0 at eisa.0
[   12.862676] Cannot allocate resource for EISA slot 1
[   12.862678] Cannot allocate resource for EISA slot 2
[   12.862704] EISA: Detected 0 cards.
[   12.862709] cpuidle: using governor ladder
[   12.862711] cpuidle: using governor menu
[   12.862804] NET: Registered protocol family 1
[   12.862834] Using IPI No-Shortcut mode
[   12.862865] registered taskstats version 1
[   12.862963]   Magic number: 5:144:925
[   12.863035]   hash matches device ptyxa
[   12.863096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.863098] EDD information not available.
[   12.863274] Freeing unused kernel memory: 368k freed
[   12.863301] Write protecting the kernel read-only data: 806k
[   12.906461] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   14.084168] fuse init (API version 7.9)
[   14.103732] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.103739] ACPI: Processor [CPU0] (supports 8 throttling states)
[   14.103754] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.109892] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.113070] ACPI: Thermal Zone [THRM] (54 C)
[   14.723758] usbcore: registered new interface driver usbfs
[   14.723784] usbcore: registered new interface driver hub
[   14.735422] usbcore: registered new device driver usb
[   14.748108] USB Universal Host Controller Interface driver v3.0
[   14.748181] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   14.748193] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.748198] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.748463] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   14.748500] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   14.748642] usb usb1: configuration #1 chosen from 1 choice
[   14.748665] hub 1-0:1.0: USB hub found
[   14.748671] hub 1-0:1.0: 2 ports detected
[   14.852034] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   14.852048] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.852053] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.852077] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   14.852113] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   14.852231] usb usb2: configuration #1 chosen from 1 choice
[   14.852254] hub 2-0:1.0: USB hub found
[   14.852260] hub 2-0:1.0: 2 ports detected
[   14.852515] SCSI subsystem initialized
[   14.899865] libata version 3.00 loaded.
[   14.955890] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.955905] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.955910] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.955937] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.955974] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   14.956089] usb usb3: configuration #1 chosen from 1 choice
[   14.956111] hub 3-0:1.0: USB hub found
[   14.956117] hub 3-0:1.0: 2 ports detected
[   15.059747] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   15.059761] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   15.059766] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   15.059790] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   15.059827] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[   15.059947] usb usb4: configuration #1 chosen from 1 choice
[   15.059970] hub 4-0:1.0: USB hub found
[   15.059975] hub 4-0:1.0: 2 ports detected
[   15.163823] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   15.163840] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.163845] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.163871] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   15.167778] ehci_hcd 0000:00:1d.7: debug port 1
[   15.167785] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   15.167792] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0544000
[   15.183502] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.183621] usb usb5: configuration #1 chosen from 1 choice
[   15.183644] hub 5-0:1.0: USB hub found
[   15.183651] hub 5-0:1.0: 8 ports detected
[   15.287563] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 18 (level, low) -> IRQ 18
[   15.307343] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   15.307354] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   15.307362] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   15.307369] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   15.347326] ssb: Sonics Silicon Backplane found on PCI device 0000:0a:03.0
[   15.347459] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   15.347498] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.347511] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   15.354201] ata_piix 0000:00:1f.2: version 2.12
[   15.354209] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   15.507080] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   15.507124] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.507214] scsi0 : ata_piix
[   15.507422] scsi1 : ata_piix
[   15.507563] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   15.507566] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   15.671291] ata1.00: ATA-7: TOSHIBA MK8034GSX, AH301J, max UDMA/100
[   15.671296] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   15.679283] ata1.00: configured for UDMA/100
[   15.938490] Clocksource tsc unstable (delta = -2284426388 ns)
[   15.942624] Time: hpet clocksource has been installed.
[   15.952923] ata2.00: ATAPI: Optiarc DVD RW AD-7530A, EX31, max UDMA/33
[   16.002517] ata2.00: configured for UDMA/33
[   16.002637] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[   16.003930] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX31 PQ: 0 ANSI: 5
[   16.016406] Driver 'sd' needs updating - please use bus_type methods
[   16.016497] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   16.016511] sd 0:0:0:0: [sda] Write Protect is off
[   16.016514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.016531] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.016579] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   16.016589] sd 0:0:0:0: [sda] Write Protect is off
[   16.016591] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.016607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.016611]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.043525]  sda1 sda2 sda3 < sda5 >
[   16.072415] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.078416] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.078437] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   16.089277] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.089283] Uniform CD-ROM driver Revision: 3.20
[   16.089339] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.330614] Attempting manual resume
[   16.330619] swsusp: Resume From Partition 8:5
[   16.330621] PM: Checking swsusp image.
[   16.330888] PM: Resume from disk failed.
[   16.379405] kjournald starting.  Commit interval 5 seconds
[   16.379419] EXT3-fs: mounted filesystem with ordered data mode.
[   25.455052] Linux agpgart interface v0.102
[   25.566982] agpgart: Detected an Intel 945GM Chipset.
[   25.567286] agpgart: Detected 7932K stolen memory.
[   25.654830] agpgart: AGP aperture is 256M @ 0xc0000000
[   25.706846] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.928120] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.110981] input: Power Button (FF) as /devices/virtual/input/input2
[   26.122158] ACPI: Power Button (FF) [PWRF]
[   26.122297] input: Lid Switch as /devices/virtual/input/input3
[   26.122402] ACPI: Lid Switch [LID]
[   26.122463] input: Power Button (CM) as /devices/virtual/input/input4
[   26.138116] ACPI: Power Button (CM) [PWRB]
[   26.138176] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.154101] ACPI: Sleep Button (CM) [SLPB]
[   26.157629] ACPI: AC Adapter [ACAD] (on-line)
[   26.503967] ACPI: Battery Slot [BAT1] (battery present)
[   26.841345] ACPI: WMI-Acer: Mapper loaded
[   26.965844] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   26.977015] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   27.644088] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   27.644098] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.644125] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   27.644162] sky2 0000:02:00.0: v1.20 addr 0x30000000 irq 16 Yukon-FE (0xb7) rev 1
[   27.644603] sky2 eth0: addr 00:16:36:d1:4d:45
[   28.117039] iTCO_vendor_support: vendor-support=0
[   28.164325] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.164461] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   28.164510] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.279767] intel_rng: FWH not detected
[   28.524707] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.524741] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.702858] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110]
[   28.702884] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.702886] Yenta: Routing CardBus interrupts to PCI
[   28.702892] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   28.929147] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   28.935238] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   28.935241] Socket status: 30000006
[   28.935244] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   28.935249] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   28.971913] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19
[   29.533199] b43-phy0: Broadcom 4318 WLAN found
[   29.573569] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   29.573592] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   29.606197] phy0: Selected rate control algorithm 'simple'
[   29.679807] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   29.679815] acer_acpi: Detected Acer WMID interface
[   30.175698] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   30.233154] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   31.265520] cs: IO port probe 0x100-0x3af: clean.
[   31.267554] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.268412] cs: IO port probe 0x820-0x8ff: clean.
[   31.269111] cs: IO port probe 0xc00-0xcf7: clean.
[   31.269971] cs: IO port probe 0xa00-0xaff: clean.
[   31.412170] lp: driver loaded but no devices found
[   31.601818] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k
[   44.107817] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   44.108030] EXT3 FS on sda2, internal journal
[   44.937695] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.481924] ACPI: ACPI Dock Station Driver 
[   46.535135] apm: BIOS not found.
[   46.646566] ppdev: user-space parallel port driver
[   46.773790] audit(1239083801.133:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5111 profile="/usr/sbin/cupsd" namespace="default"
[   48.372285] input: b43-phy0 as /devices/virtual/input/input9
[   48.608715] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   49.409033] b43-phy0 debug: Chip initialized
[   49.409427] b43-phy0 debug: 32-bit DMA initialized
[   49.416902] Registered led device: b43-phy0:tx
[   49.417102] Registered led device: b43-phy0:rx
[   49.417229] Registered led device: b43-phy0:radio
[   49.417265] b43-phy0 debug: Wireless interface started
[   49.438605] b43-phy0: Radio hardware status changed to DISABLED
[   49.438807] b43-phy0 debug: Adding Interface type 2
[   49.457604] sky2 eth0: enabling interface
[   50.457800] NET: Registered protocol family 17
[   51.014569] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   51.884596] [drm] Initialized drm 1.1.0 20060810
[   51.888060] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   51.888070] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   51.888152] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.300359] NET: Registered protocol family 10
[   59.300809] lo: Disabled Privacy Extensions
[   59.302008] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.422630] eth0: no IPv6 routers present

---

### Post by khelben1979 on 2009-04-07
What soundcard/soundchip are you able to choose from this list:
```
sudo alsaconf
```

The list that the dmesg command didn't give me anything useful to look at (maybe it's in there somewhere... Uh!)

---

### Post by Prium on 2009-04-07
Hmmm...my ubuntu doesn't seem to recognize "sudo alsaconf". I get: "**bash: alsaconf: command not found**"

In System -> Prefs. -> Sound Prefs. these are the available drivers for music and playback (bold is currently used):

**ALSA - Advanced Linux Sound Architecture** 
ALC883 Digital
ALC883 Analog
OSS - Open Sound System
PulseAudio Sound Server

In MPlayer I tried changing the audio driver also to ALSA. I think it has improved the volume slightly. Maybe it's just a matter of trying different combinations?

---

### Post by khelben1979 on 2009-04-07
> **Prium said:**
> In MPlayer I tried changing the audio driver also to ALSA. I think it has improved the volume slightly. Maybe it's just a matter of trying different combinations?

Maybe, but I'm afraid that your maximum volume with the Ubuntu system will not get the max volume that you'll get with a Windows system on that computer.

I installed Ubuntu for one of my brothers last year and I experienced the same problem which you are experience'ing now.

---

