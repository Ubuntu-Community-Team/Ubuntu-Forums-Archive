---
title: "TV-tuner Compro Videomate TV PVR/FM"
date: 2010-05-06
forum: Multimedia Software
---

### Post by proggy on 2010-05-06
I never got  that card to work In Ubuntu , this is how i`m plugged in from my setop  box by coax cable to my tv tuner card .
In windows i have no problem using the drivers provided by compro.
It would be really cool if i got that card working in Ubuntu

---

### Post by xc3RnbFO8P on 2010-05-06
In Terminal show the output of:
> lspci -vnn
and 
> dmesg

---

### Post by proggy on 2010-05-06
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
    Subsystem: ASUSTeK Computer Inc. Device [1043:826d]
    Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8249]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:81ef]
    Flags: bus master, 66MHz, medium devsel, latency 0

---

### Post by proggy on 2010-05-06
[    2.801313] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input5
[    2.801512] generic-usb 0003:046D:C01D.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-2/input0
[    6.180160] usb-storage: device scan complete
[    6.180622] scsi 6:0:0:0: Direct-Access     WD       6400AAC External 1.75 PQ: 0 ANSI: 4
[    6.181052] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    6.182119] sd 6:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    6.182604] sd 6:0:0:0: [sdb] Write Protect is off
[    6.182606] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.182608] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.183730] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.183733]  sdb: sdb1
[    6.185600] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.185604] sd 6:0:0:0: [sdb] Attached SCSI disk
[    6.510454] usb-storage: device scan complete
[    6.510913] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[    6.511283] scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[    6.511820] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    6.517282] sd 7:0:0:0: [sdc] 1994385 512-byte logical blocks: (1.02 GB/973 MiB)
[    6.525150] sd 7:0:0:0: [sdc] Write Protect is off
[    6.525152] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    6.525153] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    6.529151] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[    6.529223] sr 7:0:0:1: Attached scsi CD-ROM sr2
[    6.529334] sr 7:0:0:1: Attached scsi generic sg5 type 5
[    6.545532] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    6.545536]  sdc: sdc1
[    6.559032] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    6.559036] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    6.780363] usb-storage: device scan complete
[    6.781323] scsi 8:0:0:0: Direct-Access     Verbatim TUFF N TINY      5.00 PQ: 0 ANSI: 0 CCS
[    6.781839] sd 8:0:0:0: Attached scsi generic sg6 type 0
[    6.782691] sd 8:0:0:0: [sdd] 15642624 512-byte logical blocks: (8.00 GB/7.45 GiB)
[    6.783185] sd 8:0:0:0: [sdd] Write Protect is off
[    6.783187] sd 8:0:0:0: [sdd] Mode Sense: 23 00 00 00
[    6.783188] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[    6.785184] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[    6.785186]  sdd: sdd1
[    6.787269] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[    6.787273] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[    8.717163] kjournald starting.  Commit interval 5 seconds
[    8.717180] EXT3-fs: recovery complete.
[    8.717543] EXT3-fs: mounted filesystem with ordered data mode.
[   26.626744] udev: starting version 151
[   26.725164] vga16fb: initializing
[   26.725168] vga16fb: mapped to 0xffff8800000a0000
[   26.725231] fb0: VGA16 VGA frame buffer device
[   26.768253] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   26.768257] Disabling lock debugging due to kernel taint
[   26.811173] lp: driver loaded but no devices found
[   26.857239] EXT3 FS on sda3, internal journal
[   26.936179] type=1505 audit(1273134731.473:2):  operation="profile_load" pid=744 name="/sbin/dhclient3"
[   26.936367] type=1505 audit(1273134731.473:3):  operation="profile_load" pid=744 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.936472] type=1505 audit(1273134731.473:4):  operation="profile_load" pid=744 name="/usr/lib/connman/scripts/dhclient-script"
[   26.951445] type=1505 audit(1273134731.493:5):  operation="profile_load" pid=765 name="/usr/sbin/ntpd"
[   26.952075] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   26.953373] [fglrx] Maximum main memory to use for locked dma buffers: 5784 MBytes.
[   26.953509] [fglrx]   vendor: 1002 device: 9442 count: 1
[   26.954133] [fglrx] ioport: bar 4, base 0xde00, size: 0x100
[   26.954147] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.954151] pci 0000:01:00.0: setting latency timer to 64
[   26.954284] [fglrx] Kernel PAT support is enabled
[   26.954308] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   26.955710] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   26.956156] parport_pc 00:0a: reported by Plug and Play ACPI
[   26.956189] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   26.958174] EDAC MC: Ver: 2.1.0 Apr 28 2010
[   27.029494] Linux video capture interface: v2.00
[   27.031706] lp0: using parport0 (interrupt-driven).
[   27.055711] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
[   27.067197] ppdev: user-space parallel port driver
[   27.070857] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   27.070864] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   27.070865]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   27.070866]  (Note that use of the override may cause unknown side effects.)
[   27.070890] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   27.086060] saa7130/34: v4l2 driver version 0.2.15 loaded
[   27.139185]   alloc irq_desc for 21 on node 0
[   27.139188]   alloc kstat_irqs on node 0
[   27.139198] saa7134 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   27.139205] saa7130[0]: found at 0000:03:06.0, rev: 1, irq: 21, latency: 64, mmio: 0xfdeff000
[   27.139211] saa7130[0]: subsystem: 185b:c100, board: Compro VideoMate TV PVR/FM [card=40,autodetected]
[   27.139235] saa7130[0]: board init: gpio is 4c0000
[   27.139345] input: saa7134 IR (Compro VideoMate TV as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/input/input6
[   27.139397] IRQ 21/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   27.143602] Console: switching to colour frame buffer device 80x30
[   27.205639] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.310031] saa7130[0]: i2c eeprom 00: 5b 18 00 c1 ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310038] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310043] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310048] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310054] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310059] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff 04 ff 00 05 30 31 cb
[   27.310064] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310070] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310075] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310080] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310085] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310091] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310096] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310101] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310106] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310112] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.310118] i2c i2c-1: Invalid 7-bit address 0x7a
[   27.350102] All bytes are equal. It is not a TEA5767
[   27.350193] tuner 1-0060: chip found @ 0xc0 (saa7130[0])
[   27.372165] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   27.381553] tuner-simple 1-0060: creating new instance
[   27.381556] tuner-simple 1-0060: type set to 17 (Philips NTSC_M (MK2))
[   27.400181] saa7130[0]: registered device video0 [v4l2]
[   27.400205] saa7130[0]: registered device vbi0
[   27.400226] saa7130[0]: registered device radio0
[   27.403123] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   27.403184] HDA Intel 0000:01:00.1: setting latency timer to 64
[   27.407190] saa7134 ALSA driver for DMA sound loaded
[   27.407195] saa7130[0]/alsa: Compro VideoMate TV PVR/FM doesn't support digital audio
[   27.465439] type=1505 audit(1273134732.003:6):  operation="profile_load" pid=1020 name="/usr/share/gdm/guest-session/Xsession"
[   27.466861] type=1505 audit(1273134732.003:7):  operation="profile_replace" pid=1021 name="/sbin/dhclient3"
[   27.467060] type=1505 audit(1273134732.003:8):  operation="profile_replace" pid=1021 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.467172] type=1505 audit(1273134732.003:9):  operation="profile_replace" pid=1021 name="/usr/lib/connman/scripts/dhclient-script"
[   27.470138] type=1505 audit(1273134732.013:10):  operation="profile_load" pid=1022 name="/usr/bin/evince"
[   27.472718] type=1505 audit(1273134732.013:11):  operation="profile_load" pid=1022 name="/usr/bin/evince-previewer"
[   27.483939] r8169: eth0: link up
[   27.483947] r8169: eth0: link up
[   27.882749]   alloc irq_desc for 27 on node 0
[   27.882752]   alloc kstat_irqs on node 0
[   27.882761] fglrx_pci 0000:01:00.0: irq 27 for MSI/MSI-X
[   27.883315] [fglrx] Firegl kernel thread PID: 1253
[   27.883527] [fglrx] IRQ 27 Enabled
[   28.946255] CPU0 attaching NULL sched-domain.
[   28.946261] CPU1 attaching NULL sched-domain.
[   29.020074] CPU0 attaching sched-domain:
[   29.020077]  domain 0: span 0-1 level MC
[   29.020079]   groups: 0 1
[   29.020082] CPU1 attaching sched-domain:
[   29.020084]  domain 0: span 0-1 level MC
[   29.020085]   groups: 1 0
[   29.277054] [fglrx] Gart USWC size:1279 M.
[   29.277057] [fglrx] Gart cacheable size:508 M.
[   29.277062] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   29.277064] [fglrx] Reserved FB block: Unshared offset:fbff000, size:401000 
[   29.277066] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   32.617723] CPU0 attaching NULL sched-domain.
[   32.617729] CPU1 attaching NULL sched-domain.
[   32.670099] CPU0 attaching sched-domain:
[   32.670104]  domain 0: span 0-1 level MC
[   32.670106]   groups: 0 1
[   32.670111] CPU1 attaching sched-domain:
[   32.670112]  domain 0: span 0-1 level MC
[   32.670114]   groups: 1 0
[   33.426870] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   37.600021] eth0: no IPv6 routers present
[   55.778242] end_request: I/O error, dev fd0, sector 0
[   67.868402] end_request: I/O error, dev fd0, sector 0
[   89.810023] Clocksource tsc unstable (delta = -325421092 ns)
[ 3160.336251] CPU0 attaching NULL sched-domain.
[ 3160.336266] CPU1 attaching NULL sched-domain.
[ 3160.390154] CPU0 attaching sched-domain:
[ 3160.390163]  domain 0: span 0-1 level MC
[ 3160.390169]   groups: 0 1
[ 3160.390181] CPU1 attaching sched-domain:
[ 3160.390186]  domain 0: span 0-1 level MC
[ 3160.390190]   groups: 1 0
[ 3162.842666] PM: Syncing filesystems ... done.
[ 3162.932399] PM: Preparing system for mem sleep
[ 3162.932403] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 3162.933581] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 3162.933662] PM: Entering mem sleep
[ 3162.933673] Suspending console(s) (use no_console_suspend to debug)
[ 3162.970058] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 3162.999715] sd 2:0:0:0: [sda] Stopping disk
[ 3163.142597] PM: suspend of drv:sd dev:2:0:0:0 complete after 172.539 msecs
[ 3163.670020] PM: suspend of drv:atkbd dev:serio0 complete after 469.941 msecs
[ 3163.670986] ACPI handle has no context!
[ 3163.671129] parport_pc 00:0a: disabled
[ 3163.671242] serial 00:09: disabled
[ 3163.671343] ACPI handle has no context!
[ 3163.800050] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 3163.800083] ACPI handle has no context!
[ 3163.820021] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 129.985 msecs
[ 3163.820090] [fglrx] IRQ 27 Disabled
[ 3163.820106] [fglrx] Preparing suspend fglrx in kernel.
[ 3164.502461] [fglrx] Suspending fglrx in kernel completed.
[ 3164.502465] [fglrx] Power down the ASIC .
[ 3164.502511] PM: suspend of drv:fglrx_pci dev:0000:01:00.0 complete after 682.484 msecs
[ 3164.610108] HDA Intel 0000:00:14.2: PCI INT A disabled
[ 3164.630024] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 127.485 msecs
[ 3164.630122] ehci_hcd 0000:00:13.5: PCI INT D disabled
[ 3164.630133] ohci_hcd 0000:00:13.4: PCI INT C disabled
[ 3164.630142] ohci_hcd 0000:00:13.3: PCI INT B disabled
[ 3164.630152] ohci_hcd 0000:00:13.2: PCI INT C disabled
[ 3164.630161] ohci_hcd 0000:00:13.1: PCI INT B disabled
[ 3164.630171] ohci_hcd 0000:00:13.0: PCI INT A disabled
[ 3164.710131] ahci 0000:00:12.0: PCI INT A disabled
[ 3164.710360] PM: suspend of devices complete after 1776.469 msecs
[ 3164.710362] PM: suspend devices took 1.780 seconds
[ 3164.710986] r8169 0000:02:00.0: PME# enabled
[ 3164.750263] PM: late suspend of devices complete after 39.896 msecs
[ 3164.750333] ACPI: Preparing to enter system sleep state S3
[ 3164.790013] Disabling non-boot CPUs ...
[ 3164.790032] CPU0 attaching NULL sched-domain.
[ 3164.790034] CPU1 attaching NULL sched-domain.
[ 3164.950018] CPU0 attaching NULL sched-domain.
[ 3164.951176] Broke affinity for irq 17
[ 3164.951201] Broke affinity for irq 19
[ 3164.951226] Broke affinity for irq 22
[ 3165.060019] CPU 1 is now offline
[ 3165.060020] SMP alternatives: switching to UP code
[ 3165.064032] Back to C!
[ 3165.064032] PCI-DMA: Resuming GART IOMMU
[ 3165.064032] PCI-DMA: Restoring GART aperture settings
[ 3165.064032] Enabling non-boot CPUs ...
[ 3165.064032] SMP alternatives: switching to SMP code
[ 3165.064032] Booting processor 1 APIC 0x1 ip 0x6000
[ 3165.063671] Initializing CPU#1
[ 3165.063671] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 3165.063671] CPU: L2 Cache: 512K (64 bytes/line)
[ 3165.063671] CPU 1/0x1 -> Node 0
[ 3165.063671] CPU: Physical Processor ID: 0
[ 3165.063671] CPU: Processor Core ID: 1
[ 3165.220042] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 02
[ 3165.220108] CPU0 attaching NULL sched-domain.
[ 3165.290021] CPU0 attaching sched-domain:
[ 3165.290024]  domain 0: span 0-1 level MC
[ 3165.290025]   groups: 0 1
[ 3165.290028] CPU1 attaching sched-domain:
[ 3165.290029]  domain 0: span 0-1 level MC
[ 3165.290030]   groups: 1 0
[ 3165.290270] CPU1 is up
[ 3165.290363] ACPI: Waking up from system sleep state S3
[ 3165.290566] pci 0000:00:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 3165.290585] pcieport 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 3165.290610] pcieport 0000:00:07.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 3165.290650] ahci 0000:00:12.0: restoring config space at offset 0x2 (was 0x1018f00, writing 0x1060100)
[ 3165.290670] ahci 0000:00:12.0: set SATA to AHCI mode
[ 3165.290695] ohci_hcd 0000:00:13.0: restoring config space at offset 0x1 (was 0x2a00007, writing 0x2a00003)
[ 3165.290723] ohci_hcd 0000:00:13.1: restoring config space at offset 0x1 (was 0x2a00007, writing 0x2a00003)
[ 3165.290752] ohci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2a00007, writing 0x2a00003)
[ 3165.290780] ohci_hcd 0000:00:13.3: restoring config space at offset 0x1 (was 0x2a00007, writing 0x2a00003)
[ 3165.290809] ohci_hcd 0000:00:13.4: restoring config space at offset 0x1 (was 0x2a00007, writing 0x2a00003)
[ 3165.290842] ehci_hcd 0000:00:13.5: restoring config space at offset 0x3 (was 0x4008, writing 0x4010)
[ 3165.290847] ehci_hcd 0000:00:13.5: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[ 3165.291280] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x103, writing 0x3)
[ 3165.291300] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
[ 3165.291410] fglrx_pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x105)
[ 3165.291416] fglrx_pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfdcc0000)
[ 3165.291422] fglrx_pci 0000:01:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xde01)
[ 3165.291427] fglrx_pci 0000:01:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfdce0004)
[ 3165.291431] fglrx_pci 0000:01:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xd000000c)
[ 3165.291435] fglrx_pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800008)
[ 3165.291440] fglrx_pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100403)
[ 3165.291478] HDA Intel 0000:01:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x205)
[ 3165.291491] HDA Intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xfdcfc004)
[ 3165.291495] HDA Intel 0000:01:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800008)
[ 3165.291500] HDA Intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[ 3165.291534] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 3165.291548] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfdbff004)
[ 3165.291554] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xee01)
[ 3165.291558] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3165.291563] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 3165.291611] saa7134 0000:03:06.0: restoring config space at offset 0xf (was 0xffff01b7, writing 0xffff01ff)
[ 3165.291633] saa7134 0000:03:06.0: restoring config space at offset 0x4 (was 0xffb3fc00, writing 0xfdeff000)
[ 3165.291637] saa7134 0000:03:06.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 3165.291644] saa7134 0000:03:06.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[ 3165.292202] PM: early resume of devices complete after 1.741 msecs
[ 3165.292590] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 3165.292744] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3165.320018] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 3165.350025] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3165.380023] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 3165.410023] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3165.440024] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 3165.440975] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3165.601577] PM: resume of drv:HDA Intel dev:0000:00:14.2 complete after 160.605 msecs
[ 3165.601660] fglrx_pci 0000:01:00.0: setting latency timer to 64
[ 3165.622805] [fglrx] Power up the ASIC
[ 3165.622815] [fglrx] Preparing resume fglrx in kernel.
[ 3165.623359] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[ 3165.623362] ata1.01: ACPI cmd ef/03:42:00:00:00:b0 (SET FEATURES) filtered out
[ 3165.684481] ata4: SATA link down (SStatus 0 SControl 300)
[ 3165.684511] ata5: SATA link down (SStatus 0 SControl 300)
[ 3165.684538] ata6: SATA link down (SStatus 0 SControl 300)
[ 3165.685016] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 3165.685018] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[ 3165.686876] [fglrx] Resuming fglrx in kernel completed.
[ 3165.686991] [fglrx] IRQ 27 Enabled
[ 3165.687008] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3165.687013] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 3165.687035] r8169 0000:02:00.0: PME# disabled
[ 3165.687045] saa7130[0]: board init: gpio is 4c0000
[ 3165.720423] ata1.00: configured for UDMA/33
[ 3165.760429] ata1.01: configured for UDMA/33
[ 3165.810031] i2c 1-0061: parent i2c-1 should not be sleeping
[ 3165.810052] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[ 3165.810111] PM: resume of drv:saa7134 dev:0000:03:06.0 complete after 123.060 msecs
[ 3165.810703] serial 00:09: activated
[ 3165.811231] parport_pc 00:0a: activated
[ 3165.990017] PM: resume of drv:usb dev:usb1 complete after 178.312 msecs
[ 3166.100028] PM: resume of drv:usb dev:usb2 complete after 109.996 msecs
[ 3166.210025] PM: resume of drv:usb dev:usb3 complete after 109.982 msecs
[ 3169.210011] 
[ 3169.210012] floppy driver state
[ 3169.210013] -------------------
[ 3169.210015] now=4295254217 last interrupt=4294944082 diff=310135 last called handler=ffffffffa0038ca0
[ 3169.210016] timeout_message=lock fdc
[ 3169.210017] last output bytes:
[ 3169.210018] c1 90 4294943942
[ 3169.210019] 10 90 4294943942
[ 3169.210020]  7 80 4294943942
[ 3169.210021]  0 90 4294943942
[ 3169.210022]  8 81 4294943974
[ 3169.210023]  3 80 4294943976
[ 3169.210024] d1 90 4294943976
[ 3169.210025]  a 90 4294943976
[ 3169.210026]  7 80 4294943976
[ 3169.210027]  0 90 4294943976
[ 3169.210028]  8 81 4294944016
[ 3169.210028]  3 80 4294944018
[ 3169.210029] c1 90 4294944018
[ 3169.210030] 10 90 4294944018
[ 3169.210031]  7 80 4294944018
[ 3169.210032]  0 90 4294944018
[ 3169.210033]  8 81 4294944050
[ 3169.210034]  7 80 4294944050
[ 3169.210035]  0 90 4294944050
[ 3169.210036]  8 81 4294944082
[ 3169.210037] last result at 4294944082
[ 3169.210038] last redo_fd_request at 4294944082
[ 3169.210038] 70  0 
[ 3169.210047] status=0
[ 3169.210047] fdc_busy=1
[ 3169.210048] do_floppy=ffffffffa00338e0
[ 3169.210049] cont=ffffffffa003b340
[ 3169.210050] current_req=(null)
[ 3169.210051] command_status=-1
[ 3169.210052] 
[ 3169.210054] floppy0: floppy timeout called
[ 3169.210065] PM: resume of drv:floppy dev:floppy.0 complete after 2999.846 msecs
[ 3169.340035] PM: resume of drv:usb dev:1-9 complete after 129.888 msecs
[ 3169.530022] usb 1-10: reset high speed USB device using ehci_hcd and address 6
[ 3169.685072] PM: resume of drv:usb dev:1-10 complete after 345.016 msecs
[ 3169.685097] sd 2:0:0:0: [sda] Starting disk
[ 3171.140015] ata3: softreset failed (device not ready)
[ 3171.140018] ata3: applying SB600 PMP SRST workaround and retrying
[ 3171.320026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 3171.528160] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 3171.586468] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 3171.586470] ata3.00: configured for UDMA/133
[ 3171.626075] PM: resume of drv:sd dev:2:0:0:0 complete after 1940.979 msecs
[ 3171.990018] usb 2-2: reset low speed USB device using ohci_hcd and address 2
[ 3172.333975] PM: resume of drv:usb dev:2-2 complete after 707.855 msecs
[ 3172.700018] usb 3-2: reset low speed USB device using ohci_hcd and address 2
[ 3173.039946] PM: resume of drv:usb dev:3-2 complete after 705.921 msecs
[ 3173.040249] PM: resume of devices complete after 7747.992 msecs
[ 3173.040368] PM: resume devices took 7.750 seconds
[ 3173.040392] PM: Finishing wakeup.
[ 3173.040393] Restarting tasks ... 
[ 3173.040467] usb 1-3: USB disconnect, address 3
[ 3173.063074] done.
[ 3173.355743] r8169: eth0: link up
[ 3173.355751] r8169: eth0: link up
[ 3173.981286] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 3174.132449] usb 1-3: configuration #1 chosen from 1 choice
[ 3174.137956] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3174.138128] usb 1-9: USB disconnect, address 5
[ 3174.139925] usb-storage: device found at 7
[ 3174.139928] usb-storage: waiting for device to settle before scanning
[ 3174.300023] usb 1-9: new high speed USB device using ehci_hcd and address 8
[ 3174.451101] usb 1-9: configuration #1 chosen from 1 choice
[ 3174.454983] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3174.455130] usb-storage: device found at 8
[ 3174.455131] usb-storage: waiting for device to settle before scanning
[ 3174.789329] CPU0 attaching NULL sched-domain.
[ 3174.789345] CPU1 attaching NULL sched-domain.
[ 3174.841347] CPU0 attaching sched-domain:
[ 3174.841351]  domain 0: span 0-1 level MC
[ 3174.841353]   groups: 0 1
[ 3174.841358] CPU1 attaching sched-domain:
[ 3174.841359]  domain 0: span 0-1 level MC
[ 3174.841361]   groups: 1 0
[ 3179.131537] usb-storage: device scan complete
[ 3179.132119] scsi 9:0:0:0: Direct-Access     WD       6400AAC External 1.75 PQ: 0 ANSI: 4
[ 3179.133960] sd 9:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[ 3179.134761] sd 9:0:0:0: [sdb] Write Protect is off
[ 3179.134769] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 3179.134775] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3179.135670] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 3179.142260] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3179.142271]  sdb: sdb1
[ 3179.164325] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3179.164335] sd 9:0:0:0: [sdb] Attached SCSI disk
[ 3179.450465] usb-storage: device scan complete
[ 3179.453528] scsi 10:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[ 3179.454000] scsi 10:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[ 3179.458589] sd 10:0:0:0: Attached scsi generic sg4 type 0
[ 3179.464428] sd 10:0:0:0: [sdc] 1994385 512-byte logical blocks: (1.02 GB/973 MiB)
[ 3179.474916] sd 10:0:0:0: [sdc] Write Protect is off
[ 3179.474925] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 3179.474931] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 3179.491345] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 3179.491636] sr 10:0:0:1: Attached scsi CD-ROM sr2
[ 3179.491794] sr 10:0:0:1: Attached scsi generic sg5 type 5
[ 3179.505419] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 3179.505433]  sdc: sdc1
[ 3179.552021] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 3179.552033] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[ 3180.136815] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 3180.173202] ISOFS: changing to secondary root
[ 3183.870033] eth0: no IPv6 routers present

---

### Post by xc3RnbFO8P on 2010-05-06
Try **TVtime**, see if it works, if it don't you may have to change card and tuner number.

---

### Post by proggy on 2010-05-06
Well i tried TvTime before , but thanks for the tip ;). Didn`t work.
So how do i change the card and tuner number?:-k

---

### Post by Mze on 2010-05-06
here's a [thread]("http://newyork.ubuntuforums.org/showthread.php?t=1256845") from the forum from Sept 2009

searched via Google

---

### Post by proggy on 2010-05-07
Saw that by google search already, tried to follow the instructions but they seem incomplete to me.
Thanks for the effort.
Anyone else?

---

### Post by xc3RnbFO8P on 2010-05-07
Try:
> sudo modprobe saa7174 card=40 tuner=17 alsa=1
then start TVtime.

---

### Post by proggy on 2010-05-07
WARNING: All config files need .conf: /etc/modprobe.d/saa1734.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: /etc/modprobe.d/saa1734.save line 6: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/saa1734.save line 7: ignoring bad line starting with '[root@mythmaster'
WARNING: /etc/modprobe.d/saa1734.save line 15: ignoring bad line starting with 'x'
FATAL: Module saa7174 not found.

---

### Post by xc3RnbFO8P on 2010-05-07
Can you show the output of **sudo gedit /etc/modprobe.d/saa1734.save**
If you are trying to add to **/etc/modprobe.d/saa1734**
> sudo gedit /etc/modprobe.d/saa1734
you should add this:
> option saa7174 card=40 tuner=17 alsa=1

---

### Post by proggy on 2010-05-07
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134
[root@mythmaster ~]# cat /etc/modprobe.conf
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
alias snd-card-1 saa7134-alsa
options snd-card-1 index=1
options saa7134-alsa index=1
remove saa7134-alsa { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove saa7134-alsa

x

---

### Post by proggy on 2010-05-07
after adding "option saa7174 card=40 tuner=17 alsa=1"
I get this 

"alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134
[root@mythmaster ~]# cat /etc/modprobe.conf
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
alias snd-card-1 saa7134-alsa
options snd-card-1 index=1
options saa7134-alsa index=1
remove saa7134-alsa { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove saa7134-alsa

x
option saa7174 card=40 tuner=17 alsa=1 "

---

### Post by proggy on 2010-05-08
Not working :sad:! No biggie , i hardly use that card anyways even when on windoze, it just would`ve been nice to have it when i needed seeing I`m on Ubuntu most of time .
Compro seems like a sucky company , the card was given to me so no lost there. 
Compro doesn`t have [I]proprietary  drivers for Linux, not that i`m aware of anyways.
So they suck! [-(
[/I]

---

### Post by Mze on 2010-05-09
[SAA7130 TV tuner card under Linux. How To.]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux")

---

### Post by proggy on 2010-05-09
Thanks, I`ll look at that later.

---

### Post by proggy on 2010-05-18
I took the card out of my computer voila solved

---

