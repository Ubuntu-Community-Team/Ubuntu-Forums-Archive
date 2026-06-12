---
title: "Cannot connect to wireless network"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by The Toxic Mite on 2009-08-11
Hey all.

I am having trouble connecting to a wireless network on my desktop.

My wireless card is a Broadcom BCM4306 and I have the B43 driver installed.

On the NetworkManager applet, it does show my router but I cannot connect to it for some strange reason. It's not range issues I have (it's like over 65-70%), and my mother was convinced it was a software issue.

Here's the problem:

[indent]When I click on the name of my router, it tries to connect but after a minute or so, a prompt comes up asking for the key again, so I type it in; no connection yet, prompt comes up again, put in the key, and 5 or so minutes of entering the key and trying to connect, it eventually stops.[/indent]

I have managed to get it to connect ONCE before, so I don't see what's wrong.

-TTM-

---

### Post by garibaldino on 2009-08-11
isn't networkManger known to be buggy?

do you get a network connection when you use the classic ifup card_name method?

you can try wicd instead too, it has better records than nM.

here's how should look your interfaces file fo the ifup wlan0 method
```
auto wlan0
 14 iface wlan0 inet dhcp
 15 wpa-ssid XXXXXXXXX
 16 wpa-key_mgmt WPA-PSK
 17 wpa-proto WPA
 18 wpa-pairwise TKIP
 19 wpa-group TKIP
 20 wpa-psk XXXXXXXXXXX
 21 wpa-driver wext
```

---

### Post by The Toxic Mite on 2009-08-11
Tried connecting with WICD.

When I get to the confirming authentication thingy, it just hangs without connecting.

It does say 75% for the range so I can't see how I can't get it connected. :-k

---

### Post by The Toxic Mite on 2009-08-11
Bump :p

---

### Post by The Toxic Mite on 2009-08-11
Sorry for my impatience, but I really wanna get rid of Windows XP :(

---

### Post by The Toxic Mite on 2009-08-12
Bump :|

---

### Post by The Toxic Mite on 2009-08-12
Anyone?

:|

---

### Post by The Toxic Mite on 2009-08-12
...

---

### Post by fjosh on 2009-08-12
I have the exact same card and also haven't been able to get it working with either b43-fwcutter or bcmwl-kernel-source.

Bookmarked in hopes of an answer.

---

### Post by ibuclaw on 2009-08-13
Look here: [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Run dmesg and check for any output from the b43 driver, as it may say that it can't find a certain type of firmware.
> 
in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package:
sudo apt-get install b43-fwcutter
when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter)

So make sure that you are connected first before you try to install the driver in ubuntu. :)

Regards
Iain

---

### Post by The Toxic Mite on 2009-08-13
> **tinivole said:**
> Look here: [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Run dmesg and check for any output from the b43 driver, as it may say that it can't find a certain type of firmware.

So make sure that you are connected first before you try to install the driver in ubuntu. :)

Regards
Iain

Hey Iain.

On the #ubuntu-uk IRC channel, someone provided me with a link to a tar file with the firmware in it. I untarred it, and the wireless seems to be working fine but it won't connect for some odd reason.

On wicd, when it comes to the "Validating authentication..." bit, it just hangs there for two minutes or so then the connection drops. It tries to connect again, but it still hangs at that bit, and after a while it stops.

I will post the output of dmesg soon :)

Calvin

---

### Post by The Toxic Mite on 2009-08-13
Right, I have it here :)

```

[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1500.034 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1310080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242844k/262080k available (4126k kernel code, 18656k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd07f0000 - 0xff3fe000   ( 748 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3000.06 BogoMIPS (lpj=6000136)
[    0.004061] Security Framework initialized
[    0.004078] SELinux:  Disabled at boot.
[    0.004117] AppArmor: AppArmor initialized
[    0.004142] Mount-cache hash table entries: 512
[    0.004450] Initializing cgroup subsys ns
[    0.004462] Initializing cgroup subsys cpuacct
[    0.004470] Initializing cgroup subsys memory
[    0.004481] Initializing cgroup subsys freezer
[    0.004517] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004526] CPU: L2 cache: 256K
[    0.004534] CPU: Hyper-Threading is disabled
[    0.004578] Checking 'hlt' instruction... OK.
[    0.021351] SMP alternatives: switching to UP code
[    0.217556] Freeing SMP alternatives: 18k freed
[    0.217568] ACPI: Core revision 20080926
[    0.221092] ACPI: Checking initramfs for custom DSDT
[    0.811463] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.851167] CPU0: Intel(R) Pentium(R) 4 CPU 1.50GHz stepping 02
[    0.852002] Brought up 1 CPUs
[    0.852002] Total of 1 processors activated (3000.06 BogoMIPS).
[    0.852002] CPU0 attaching NULL sched-domain.
[    0.852002] net_namespace: 776 bytes
[    0.852002] Booting paravirtualized kernel on bare hardware
[    0.852002] Time: 18:05:56  Date: 08/13/09
[    0.852002] regulator: core version 0.5
[    0.852002] NET: Registered protocol family 16
[    0.852002] EISA bus registered
[    0.852002] ACPI: bus type pci registered
[    0.854973] PCI: PCI BIOS revision 2.10 entry at 0xfdb81, last bus=2
[    0.854978] PCI: Using configuration type 1 for base access
[    0.858507] ACPI: EC: Look up EC in DSDT
[    0.869214] ACPI: Interpreter enabled
[    0.869228] ACPI: (supports S0 S3 S4 S5)
[    0.869268] ACPI: Using IOAPIC for interrupt routing
[    0.878454] ACPI: No dock devices found.
[    0.878485] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.878582] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xebffffff]
[    0.878806] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.878813] pci 0000:00:1f.0: quirk: region 0400-043f claimed by ICH4 GPIO
[    0.878867] pci 0000:00:1f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.878943] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc81f]
[    0.879021] pci 0000:00:1f.3: reg 20 io port: [0xc00-0xc0f]
[    0.879094] pci 0000:00:1f.4: reg 20 io port: [0xcc00-0xcc1f]
[    0.879140] pci 0000:00:1f.5: reg 10 io port: [0xd400-0xd4ff]
[    0.879151] pci 0000:00:1f.5: reg 14 io port: [0xd000-0xd03f]
[    0.879216] pci 0000:00:1f.6: reg 10 io port: [0xdc00-0xdcff]
[    0.879227] pci 0000:00:1f.6: reg 14 io port: [0xd800-0xd87f]
[    0.879318] pci 0000:01:00.0: reg 10 32bit mmio: [0xee000000-0xeeffffff]
[    0.879329] pci 0000:01:00.0: reg 14 32bit mmio: [0xd8000000-0xdfffffff]
[    0.879358] pci 0000:01:00.0: reg 30 32bit mmio: [0xefdf0000-0xefdfffff]
[    0.879425] pci 0000:00:01.0: bridge 32bit mmio: [0xedd00000-0xefdfffff]
[    0.879432] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd5a00000-0xe5afffff]
[    0.879469] pci 0000:02:01.0: reg 10 32bit mmio: [0xefefe000-0xefefffff]
[    0.879561] pci 0000:00:1e.0: transparent bridge
[    0.879573] pci 0000:00:1e.0: bridge 32bit mmio: [0xefe00000-0xefefffff]
[    0.879581] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe5b00000-0xe5bfffff]
[    0.879599] bus 00 -> node 0
[    0.879614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.879868] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[    0.906258] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.906484] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.906703] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.906944] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[    0.907153] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.907372] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.907590] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.907810] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.908043] ACPI: Power Resource [URP1] (off)
[    0.908119] ACPI: Power Resource [URP2] (off)
[    0.908190] ACPI: Power Resource [FDDP] (off)
[    0.908266] ACPI: Power Resource [LPTP] (off)
[    0.908428] ACPI: WMI: Mapper loaded
[    0.908935] SCSI subsystem initialized
[    0.909050] libata version 3.00 loaded.
[    0.909175] usbcore: registered new interface driver usbfs
[    0.909219] usbcore: registered new interface driver hub
[    0.909291] usbcore: registered new device driver usb
[    0.909598] PCI: Using ACPI for IRQ routing
[    0.909793] Bluetooth: Core ver 2.13
[    0.909793] NET: Registered protocol family 31
[    0.909793] Bluetooth: HCI device and connection manager initialized
[    0.909793] Bluetooth: HCI socket layer initialized
[    0.909793] NET: Registered protocol family 8
[    0.909793] NET: Registered protocol family 20
[    0.909793] NetLabel: Initializing
[    0.909793] NetLabel:  domain hash size = 128
[    0.909793] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.909793] NetLabel:  unlabeled traffic allowed by default
[    0.909793] AppArmor: AppArmor Filesystem Enabled
[    0.909793] pnp: PnP ACPI init
[    0.909793] ACPI: bus type pnp registered
[    0.916840] pnp: PnP ACPI: found 12 devices
[    0.916847] ACPI: ACPI bus type pnp unregistered
[    0.916858] PnPBIOS: Disabled by ACPI PNP
[    0.951833] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.951839] pci 0000:00:01.0:   IO window: disabled
[    0.951848] pci 0000:00:01.0:   MEM window: 0xedd00000-0xefdfffff
[    0.951855] pci 0000:00:01.0:   PREFETCH window: 0x000000d5a00000-0x000000e5afffff
[    0.951864] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.951867] pci 0000:00:1e.0:   IO window: disabled
[    0.951876] pci 0000:00:1e.0:   MEM window: 0xefe00000-0xefefffff
[    0.951883] pci 0000:00:1e.0:   PREFETCH window: 0x000000e5b00000-0x000000e5bfffff
[    0.951912] pci 0000:00:1e.0: setting latency timer to 64
[    0.951919] bus: 00 index 0 io port: [0x00-0xffff]
[    0.951925] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.951930] bus: 01 index 0 mmio: [0x0-0x0]
[    0.951934] bus: 01 index 1 mmio: [0xedd00000-0xefdfffff]
[    0.951939] bus: 01 index 2 mmio: [0xd5a00000-0xe5afffff]
[    0.951943] bus: 01 index 3 mmio: [0x0-0x0]
[    0.951946] bus: 02 index 0 mmio: [0x0-0x0]
[    0.951950] bus: 02 index 1 mmio: [0xefe00000-0xefefffff]
[    0.951955] bus: 02 index 2 mmio: [0xe5b00000-0xe5bfffff]
[    0.951959] bus: 02 index 3 io port: [0x00-0xffff]
[    0.951965] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.952004] NET: Registered protocol family 2
[    0.952291] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.952799] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.952897] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.952991] TCP: Hash tables configured (established 8192 bind 8192)
[    0.952996] TCP reno registered
[    0.953238] NET: Registered protocol family 1
[    0.953543] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.537303]  it is
[    2.195594] Freeing initrd memory: 7356k freed
[    2.195753] cpufreq: No nForce2 chipset.
[    2.196130] audit: initializing netlink socket (disabled)
[    2.196174] type=2000 audit(1250186757.196:1): initialized
[    2.208275] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.210887] VFS: Disk quotas dquot_6.5.1
[    2.211038] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.212520] fuse init (API version 7.10)
[    2.212738] msgmni has been set to 488
[    2.213227] alg: No test for stdrng (krng)
[    2.213265] io scheduler noop registered
[    2.213269] io scheduler anticipatory registered
[    2.213273] io scheduler deadline registered
[    2.213341] io scheduler cfq registered (default)
[    2.213440] pci 0000:01:00.0: Boot video device
[    2.219965] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.219989] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.220292] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.220300] ACPI: Power Button (FF) [PWRF]
[    2.220402] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.220407] ACPI: Power Button (CM) [PWRB]
[    2.220511] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.220524] ACPI: Sleep Button (CM) [SLPB]
[    2.220920] processor ACPI_CPU:00: registered as cooling_device0
[    2.220930] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.225682] thermal LNXTHERM:01: registered as thermal_zone0
[    2.226060] ACPI: Thermal Zone [THRM] (50 C)
[    2.226164] isapnp: Scanning for PnP cards...
[    2.580343] isapnp: No Plug & Play device found
[    2.583476] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.583618] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.583746] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.584209] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.584419] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.584764] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.584776] serial 0000:00:1f.6: PCI INT B disabled
[    2.586322] brd: module loaded
[    2.587051] loop: module loaded
[    2.587299] Fixed MDIO Bus: probed
[    2.587313] PPP generic driver version 2.4.2
[    2.587457] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.587538] Driver 'sd' needs updating - please use bus_type methods
[    2.587561] Driver 'sr' needs updating - please use bus_type methods
[    2.587725] ata_piix 0000:00:1f.1: version 2.12
[    2.587860] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.588157] scsi0 : ata_piix
[    2.588432] scsi1 : ata_piix
[    2.591232] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.591238] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.789459] ata1.00: ATA-7: ST380215A, 3.AAD, max UDMA/100
[    2.789465] ata1.00: 156301488 sectors, multi 16: LBA48 
[    2.856136] ata1.00: configured for UDMA/100
[    3.012929] ata2.00: ATAPI: IDE DVD-ROM 16X, VER 7.50, max UDMA/33
[    3.013000] ata2.01: ATAPI: HL-DT-ST GCE-8481B, 2.03, max UDMA/33
[    3.020446] ata2.00: configured for UDMA/33
[    3.028458] ata2.01: configured for UDMA/33
[    3.029086] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[    3.029388] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.029427] sd 0:0:0:0: [sda] Write Protect is off
[    3.029432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.029487] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.029674] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.029708] sd 0:0:0:0: [sda] Write Protect is off
[    3.029713] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.029767] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.029775]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.086533] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.086670] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.087069] scsi 1:0:0:0: CD-ROM            IDE      DVD-ROM 16X      7.50 PQ: 0 ANSI: 5
[    3.088876] sr0: scsi3-mmc drive: 2x/48x cd/rw xa/form2 cdda tray
[    3.088885] Uniform CD-ROM driver Revision: 3.20
[    3.089158] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.089280] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.089705] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  2.03 PQ: 0 ANSI: 5
[    3.092643] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    3.092860] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.092974] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    3.094382] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.094446] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.094479] uhci_hcd: USB Universal Host Controller Interface driver
[    3.094599] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.094616] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.094623] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.094784] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.094839] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000c800
[    3.095049] usb usb1: configuration #1 chosen from 1 choice
[    3.095108] hub 1-0:1.0: USB hub found
[    3.095134] hub 1-0:1.0: 2 ports detected
[    3.095386] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    3.095403] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    3.095409] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    3.095521] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    3.095571] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000cc00
[    3.095752] usb usb2: configuration #1 chosen from 1 choice
[    3.095811] hub 2-0:1.0: USB hub found
[    3.095832] hub 2-0:1.0: 2 ports detected
[    3.096155] usbcore: registered new interface driver libusual
[    3.096237] usbcore: registered new interface driver usbserial
[    3.096263] USB Serial support registered for generic
[    3.096293] usbcore: registered new interface driver usbserial_generic
[    3.096298] usbserial: USB Serial Driver core
[    3.096399] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.099208] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.099222] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.099518] mice: PS/2 mouse device common for all mice
[    3.099878] rtc_cmos 00:07: RTC can wake from S4
[    3.099969] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.100034] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    3.100214] device-mapper: uevent: version 1.0.3
[    3.100541] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.100697] device-mapper: multipath: version 1.0.5 loaded
[    3.100705] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.100934] EISA: Probing bus 0 at eisa.0
[    3.100987] EISA: Detected 0 cards.
[    3.101067] cpuidle: using governor ladder
[    3.101073] cpuidle: using governor menu
[    3.102143] TCP cubic registered
[    3.102314] NET: Registered protocol family 10
[    3.103235] lo: Disabled Privacy Extensions
[    3.103912] NET: Registered protocol family 17
[    3.103974] Bluetooth: L2CAP ver 2.11
[    3.103978] Bluetooth: L2CAP socket layer initialized
[    3.103984] Bluetooth: SCO (Voice Link) ver 0.6
[    3.103988] Bluetooth: SCO socket layer initialized
[    3.104147] Bluetooth: RFCOMM socket layer initialized
[    3.104174] Bluetooth: RFCOMM TTY layer initialized
[    3.104178] Bluetooth: RFCOMM ver 1.10
[    3.104324] Using IPI No-Shortcut mode
[    3.104560] registered taskstats version 1
[    3.104785]   Magic number: 5:411:89
[    3.104922] rtc_cmos 00:07: setting system clock to 2009-08-13 18:05:58 UTC (1250186758)
[    3.104929] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.104932] EDD information not available.
[    3.106353] Freeing unused kernel memory: 532k freed
[    3.106594] Write protecting the kernel text: 4128k
[    3.106667] Write protecting the kernel read-only data: 1532k
[    3.122199] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.404053] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.571048] usb 1-1: configuration #1 chosen from 1 choice
[    3.696160] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.772596] Floppy drive(s): fd0 is 1.44M
[    3.790380] FDC 0 is a post-1991 82077
[    3.859764] usb 2-2: configuration #1 chosen from 1 choice
[    3.880151] hub 2-2:1.0: USB hub found
[    3.881515] hub 2-2:1.0: 4 ports detected
[    3.928349] b43-pci-bridge 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.944179] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[    4.165501] usb 2-2.3: new full speed USB device using uhci_hcd and address 3
[    4.436665] usb 2-2.3: configuration #1 chosen from 1 choice
[    5.096293] PM: Starting manual resume from disk
[    5.096303] PM: Resume from partition 8:7
[    5.096306] PM: Checking hibernation image.
[    5.096635] PM: Resume from disk failed.
[    5.139157] kjournald starting.  Commit interval 5 seconds
[    5.139193] EXT3-fs: mounted filesystem with ordered data mode.
[   10.465124] udev: starting version 141
[   10.649544] Linux agpgart interface v0.103
[   10.689862] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   10.694492] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   10.740532] parport_pc 00:04: reported by Plug and Play ACPI
[   10.740656] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   10.880335] intel_rng: FWH not detected
[   10.896595] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.078833] iTCO_vendor_support: vendor-support=0
[   11.082868] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.083146] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   11.083166] iTCO_wdt: No card detected
[   11.512462] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.512747] usbcore: registered new interface driver btusb
[   11.744809] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.779702] cfg80211: Calling CRDA to update world regulatory domain
[   11.906757] input: MicroTouch Systems, Inc. 3M USB Touchscreen - Dell as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input6
[   11.917250] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.936723] usbcore: registered new interface driver usbtouchscreen
[   11.985614] b43-phy0: Broadcom 4306 WLAN found
[   12.059721] phy0: Selected rate control algorithm 'pid'
[   12.194838] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   12.387868] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.387910] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.400823] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   12.501720] psmouse serio1: ID: 10 00 64<6>ppdev: user-space parallel port driver
[   12.826962] cfg80211: World regulatory domain updated:
[   12.826975]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.826982]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.826987]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.826992]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.826997]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.827002]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.960032] intel8x0_measure_ac97_clock: measured 55168 usecs
[   12.960040] intel8x0: clocking to 48000
[   13.193677] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   13.288255] lp0: using parport0 (interrupt-driven).
[   13.520990] Adding 730916k swap on /dev/sda7.  Priority:-1 extents:1 across:730916k
[   14.131357] EXT3 FS on sda6, internal journal
[   15.595564] type=1505 audit(1250183170.987:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1944
[   15.707015] type=1505 audit(1250183171.099:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1948
[   15.707575] type=1505 audit(1250183171.099:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1948
[   15.707815] type=1505 audit(1250183171.099:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1948
[   15.707989] type=1505 audit(1250183171.099:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1948
[   16.010128] type=1505 audit(1250183171.403:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1953
[   16.010875] type=1505 audit(1250183171.403:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1953
[   16.081294] type=1505 audit(1250183171.475:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1957
[   21.271513] input: b43-phy0 as /devices/virtual/input/input8
[   21.356141] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   21.438738] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   21.482648] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   21.498988] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   21.628045] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   21.691201] Registered led device: b43-phy0::tx
[   21.691244] Registered led device: b43-phy0::rx
[   21.691287] Registered led device: b43-phy0::radio
[   21.708042] b43-phy0: Radio turned on by software
[   21.708337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.914526] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.914533] Bluetooth: BNEP filters: protocol multicast
[   22.964560] Bridge firewalling registered
[   32.806648] input: b43-phy0 as /devices/virtual/input/input9
[   32.964028] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   33.020304] Registered led device: b43-phy0::tx
[   33.020346] Registered led device: b43-phy0::rx
[   33.020386] Registered led device: b43-phy0::radio
[   33.052416] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.366217] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   33.366282] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   33.433743] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   33.632059] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[   33.832026] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[   34.032033] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[   34.060026] pan0: no IPv6 routers present
[   44.928443] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   44.936154] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   45.136030] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[   45.336029] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[   45.536077] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[   56.424455] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   56.432155] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   56.632026] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[   56.832028] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[   57.032027] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[   67.928539] wlan0: authenticate with AP 00:1f:e2:9b:ea:8a
[   67.960044] wlan0: authenticate with AP 00:1f:e2:9b:ea:8a
[   68.160028] wlan0: authenticate with AP 00:1f:e2:9b:ea:8a
[   68.360024] wlan0: authenticate with AP 00:1f:e2:9b:ea:8a
[   68.361693] wlan0: authenticated
[   68.361699] wlan0: associate with AP 00:1f:e2:9b:ea:8a
[   68.560026] wlan0: associate with AP 00:1f:e2:9b:ea:8a
[   68.562430] wlan0: RX AssocResp from 00:1f:e2:9b:ea:8a (capab=0x411 status=0 aid=1)
[   68.562435] wlan0: associated
[   68.563301] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.626937] input: b43-phy0 as /devices/virtual/input/input10
[   76.784051] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   76.840324] Registered led device: b43-phy0::tx
[   76.840367] Registered led device: b43-phy0::rx
[   76.840412] Registered led device: b43-phy0::radio
[   76.872408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.920917] wlan0: deauthenticating by local choice (reason=3)
[   77.070397] input: b43-phy0 as /devices/virtual/input/input11
[   77.228033] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   77.284700] Registered led device: b43-phy0::tx
[   77.284744] Registered led device: b43-phy0::rx
[   77.284787] Registered led device: b43-phy0::radio
[   77.316411] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.325822] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   77.342698] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   77.345288] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   77.544045] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[   77.744065] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[   77.944026] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[   88.820567] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   88.828153] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[   89.028049] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[   89.228027] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[   89.428059] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[  100.316614] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  100.332246] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  100.532227] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[  100.732066] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[  100.932054] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[  111.864550] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  111.872160] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  112.073074] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[  112.272050] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[  112.472065] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[  120.741714] input: b43-phy0 as /devices/virtual/input/input12
[  120.904058] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  120.960292] Registered led device: b43-phy0::tx
[  120.960335] Registered led device: b43-phy0::rx
[  120.960378] Registered led device: b43-phy0::radio
[  120.992548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  121.403635] input: b43-phy0 as /devices/virtual/input/input13
[  121.560056] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  121.616322] Registered led device: b43-phy0::tx
[  121.616365] Registered led device: b43-phy0::rx
[  121.616406] Registered led device: b43-phy0::radio
[  121.650799] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  123.188495] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  123.196144] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  123.396031] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[  123.596026] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[  123.796035] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[  134.684451] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  134.700094] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  134.900032] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[  135.100056] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[  135.300064] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
[  146.184452] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  146.192168] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 1
[  146.392055] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 2
[  146.592065] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a try 3
[  146.792030] wlan0: direct probe to AP 00:1f:e2:9b:ea:8a timed out
calvinps@InterCity-125:~$ 

```

---

### Post by The Toxic Mite on 2009-08-14
bump

---

### Post by The Toxic Mite on 2009-08-15
bump

---

### Post by The Toxic Mite on 2009-08-16
I have decided to give up on trying to get my wireless to work on Ubuntu.

Thank you for trying to support me, guys :)

---

### Post by fjosh on 2009-08-16
> **The Toxic Mite said:**
> I have decided to give up on trying to get my wireless to work on Ubuntu.
I'm right there with you.  I wish Broadcom would step up to the situation.

---

### Post by The Toxic Mite on 2009-08-16
> **fjosh said:**
> I'm right there with you.  I wish Broadcom would step up to the situation.

I don't think it's Broadcom's fault

I just think my desktop has a crappy wireless card.

---

### Post by fjosh on 2009-08-16
> **The Toxic Mite said:**
> I don't think it's Broadcom's fault

I just think my desktop has a crappy wireless card.
I'd blame Broadcom before the people that are trying to create work-arounds for a poor driver/firmware situation.

---

### Post by ibuclaw on 2009-08-17
You are using old firmware, as far as I can see...

The wiki seems to suggest these firmware drivers are to be used for 2.6.25+ kernels: [http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
The most recent firmware being these: [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Or alternatively, after some nosing round, these seem to be known working firmware: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

All of them of which are newer than the ones you are currently using.
Lots to try, I know, but I'm not a broadcom user, so am just limited to suggestions.

Regards
Iain

---

### Post by The Toxic Mite on 2009-08-17
I tried the third link in the above post but it won't work

---

### Post by MysticGold04 on 2009-08-19
I'm also having the same issue... I had an issue with my router that was running WPA2, and wicd would connect just fine, but now my backup router only does WPA, so now it will not connect (times out) just like you have stated.  At least it seems for me an issue with WPA only, as my wireless was working with WPA2.  I am for certain using the right SSID and passphrase.

---

### Post by skaramanger on 2009-08-22
Did you Solve your problem?
I have similar hardware.  Post output (minus any sensitive info) from your /etc/network/interfaces file.

---

### Post by MysticGold04 on 2009-08-23
> **MysticGold04 said:**
> I'm also having the same issue... I had an issue with my router that was running WPA2, and wicd would connect just fine, but now my backup router only does WPA, so now it will not connect (times out) just like you have stated.  At least it seems for me an issue with WPA only, as my wireless was working with WPA2.  I am for certain using the right SSID and passphrase.


BTW, if I boot into Windows, my laptop can connect just fine.  Seems to be a Linux issue with WPA.  WPA2, however works just fine under linux and network manager/wicd.

---

