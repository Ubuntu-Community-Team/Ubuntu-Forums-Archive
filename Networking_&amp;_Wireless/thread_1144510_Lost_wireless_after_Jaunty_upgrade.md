---
title: "Lost wireless after Jaunty upgrade"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by iClouseau88 on 2009-04-30
Hi,

I just upgraded from Intrepid to Jaunty in a dual-boot XP-Ubuntu laptop with DLink WNA-2330 PCMCIA but now I only got wired connection, no more wireless connection. Network Manager says "wireless connection disconnected".  I did check that ath5k driver is NOT blacklisted.  There has been no other changes to my network settings.

System>Admin>HardwareDrivers shows "no proprietary driver found".

Please help me.  It bothers me that every time Ubuntu is upgraded Network Manager is messed with.  Why can't they leave this alone if it works?

Thanks in advance

:confused:

---

### Post by iClouseau88 on 2009-05-01
Bump!

---

### Post by t0mppa on 2009-05-01
Run the following commands on a terminal and post back with the output: ```
lshw -C network
ifconfig
```

---

### Post by iClouseau88 on 2009-05-01
Hello t0mppa,

Here's the output of my terminal.  I am wondering why ath5k (Madwifi) driver is present but not shown in System>Admin>Hardware Drivers:


hoe1@hoe1-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:8d:b4:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.10.101 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:d9:d1:f0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:26:70:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.14 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:2c:8c:22:0e:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
hoe1@hoe1-laptop:~$ ifconfig

---

### Post by iClouseau88 on 2009-05-01
OOps, forgot to include the output of "ifconfig":

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:d9:d1:f0  
          inet6 addr: fe80::215:e9ff:fed9:d1f0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:312 (312.0 B)  TX bytes:3020 (3.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:00:39:8d:b4:2c  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe8d:b42c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6512125 (6.5 MB)  TX bytes:607931 (607.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:26:70:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-D9-D1-F0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0 is my normal wireless interface, but why is it using IPv6 instead of IPv4 as in Intrepid?

I would appreciate help from fellow Ubuntu Forums users.

---

### Post by iClouseau88 on 2009-05-01
Bump!!!

---

### Post by iClouseau88 on 2009-05-01
Here's the output of dmesg:

[    0.942608] system 00:08: ioport range 0xee00-0xee7f has been reserved
[    0.942615] system 00:08: ioport range 0xee80-0xee8f has been reserved
[    0.942622] system 00:08: ioport range 0xee90-0xee9f has been reserved
[    0.942628] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[    0.942635] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[    0.977660] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.977666] pci 0000:00:01.0:   IO window: disabled
[    0.977676] pci 0000:00:01.0:   MEM window: 0xf7f00000-0xfdffffff
[    0.977684] pci 0000:00:01.0:   PREFETCH window: 0x0000003c000000-0x0000003c0fffff
[    0.977719] pci 0000:02:0c.0: CardBus bridge, secondary bus 0000:03
[    0.977726] pci 0000:02:0c.0:   IO window: 0x00d000-0x00d0ff
[    0.977734] pci 0000:02:0c.0:   IO window: 0x00d400-0x00d4ff
[    0.977742] pci 0000:02:0c.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.977750] pci 0000:02:0c.0:   MEM window: 0x40000000-0x43ffffff
[    0.977759] pci 0000:02:0d.0: CardBus bridge, secondary bus 0000:07
[    0.977764] pci 0000:02:0d.0:   IO window: 0x00d800-0x00d8ff
[    0.977772] pci 0000:02:0d.0:   IO window: 0x00dc00-0x00dcff
[    0.977781] pci 0000:02:0d.0:   PREFETCH window: 0x34000000-0x37ffffff
[    0.977789] pci 0000:02:0d.0:   MEM window: 0x44000000-0x47ffffff
[    0.977798] pci 0000:02:0d.1: CardBus bridge, secondary bus 0000:0b
[    0.977803] pci 0000:02:0d.1:   IO window: 0x001000-0x0010ff
[    0.977811] pci 0000:02:0d.1:   IO window: 0x001400-0x0014ff
[    0.977820] pci 0000:02:0d.1:   PREFETCH window: 0x38000000-0x3bffffff
[    0.977828] pci 0000:02:0d.1:   MEM window: 0x48000000-0x4bffffff
[    0.977837] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.977843] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.977853] pci 0000:00:1e.0:   MEM window: 0xf7d00000-0xf7dfffff
[    0.977861] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x0000003bffffff
[    0.977893] pci 0000:00:1e.0: setting latency timer to 64
[    0.978289] pci 0000:02:0c.0: power state changed by ACPI to D0
[    0.978300] pci 0000:02:0c.0: enabling device (0000 -> 0003)
[    0.979044] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.979051] PCI: setting IRQ 11 as level-triggered
[    0.979060] pci 0000:02:0c.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.979402] pci 0000:02:0d.0: power state changed by ACPI to D0
[    0.979412] pci 0000:02:0d.0: enabling device (0000 -> 0003)
[    0.980122] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.980130] pci 0000:02:0d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.980473] pci 0000:02:0d.1: power state changed by ACPI to D0
[    0.980483] pci 0000:02:0d.1: enabling device (0000 -> 0003)
[    0.981174] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.981182] pci 0000:02:0d.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.981197] bus: 00 index 0 io port: [0x00-0xffff]
[    0.981202] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.981207] bus: 01 index 0 mmio: [0x0-0x0]
[    0.981212] bus: 01 index 1 mmio: [0xf7f00000-0xfdffffff]
[    0.981218] bus: 01 index 2 mmio: [0x3c000000-0x3c0fffff]
[    0.981222] bus: 01 index 3 mmio: [0x0-0x0]
[    0.981227] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.981232] bus: 02 index 1 mmio: [0xf7d00000-0xf7dfffff]
[    0.981238] bus: 02 index 2 mmio: [0x30000000-0x3bffffff]
[    0.981243] bus: 02 index 3 io port: [0x00-0xffff]
[    0.981248] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.981253] bus: 03 index 0 io port: [0xd000-0xd0ff]
[    0.981258] bus: 03 index 1 io port: [0xd400-0xd4ff]
[    0.981263] bus: 03 index 2 mmio: [0x30000000-0x33ffffff]
[    0.981268] bus: 03 index 3 mmio: [0x40000000-0x43ffffff]
[    0.981274] bus: 07 index 0 io port: [0xd800-0xd8ff]
[    0.981279] bus: 07 index 1 io port: [0xdc00-0xdcff]
[    0.981284] bus: 07 index 2 mmio: [0x34000000-0x37ffffff]
[    0.981289] bus: 07 index 3 mmio: [0x44000000-0x47ffffff]
[    0.981295] bus: 0b index 0 io port: [0x1000-0x10ff]
[    0.981300] bus: 0b index 1 io port: [0x1400-0x14ff]
[    0.981305] bus: 0b index 2 mmio: [0x38000000-0x3bffffff]
[    0.981310] bus: 0b index 3 mmio: [0x48000000-0x4bffffff]
[    0.981344] NET: Registered protocol family 2
[    0.981704] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.982352] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.982737] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.983200] TCP: Hash tables configured (established 16384 bind 16384)
[    0.983210] TCP reno registered
[    0.983679] NET: Registered protocol family 1
[    0.984151] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.583061]  it is
[    2.378857] Freeing initrd memory: 7379k freed
[    2.378990] Simple Boot Flag at 0x7c set to 0x1
[    2.379106] speedstep: frequency transition measured seems out of range (4800 nSec), falling back to a safe one of 500000 nSec.
[    2.379265] cpufreq: No nForce2 chipset.
[    2.379606] audit: initializing netlink socket (disabled)
[    2.379688] type=2000 audit(1241216260.376:1): initialized
[    2.397460] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.401037] VFS: Disk quotas dquot_6.5.1
[    2.401207] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.402989] fuse init (API version 7.10)
[    2.403225] msgmni has been set to 992
[    2.403815] alg: No test for stdrng (krng)
[    2.403855] io scheduler noop registered
[    2.403860] io scheduler anticipatory registered
[    2.403865] io scheduler deadline registered
[    2.403938] io scheduler cfq registered (default)
[    2.404094] pci 0000:01:00.0: Boot video device
[    2.410628] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.410652] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.410944] ACPI: AC Adapter [ADP1] (on-line)
[    2.411879] ACPI Warning (nspredef-0858): \_SB_.BAT1._BIF: Return Package type mismatch at index 12 - found Integer, expected String/Buffer [20080926]
[    2.412457] ACPI: Battery Slot [BAT1] (battery present)
[    2.412630] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.412638] ACPI: Power Button (FF) [PWRF]
[    2.412761] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.412856] ACPI: Lid Switch [LID]
[    2.413479] fan PNP0C0B:00: registered as cooling_device0
[    2.413494] ACPI: Fan [FAN] (off)
[    2.413902] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.413942] processor ACPI_CPU:00: registered as cooling_device1
[    2.418886] thermal LNXTHERM:01: registered as thermal_zone0
[    2.419665] ACPI: Thermal Zone [THRM] (78 C)
[    2.419772] isapnp: Scanning for PnP cards...
[    2.772600] isapnp: No Plug & Play device found
[    2.776159] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.776298] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.777012] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.777235] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.777252] serial 0000:00:1f.6: PCI INT B disabled
[    2.779004] brd: module loaded
[    2.779798] loop: module loaded
[    2.780164] Fixed MDIO Bus: probed
[    2.780183] PPP generic driver version 2.4.2
[    2.780359] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.780454] Driver 'sd' needs updating - please use bus_type methods
[    2.780478] Driver 'sr' needs updating - please use bus_type methods
[    2.780677] ata_piix 0000:00:1f.1: version 2.12
[    2.780847] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.781154] scsi0 : ata_piix
[    2.781522] scsi1 : ata_piix
[    2.782805] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xcff0 irq 14
[    2.782813] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xcff8 irq 15
[    2.944613] ata1.00: ATA-5: IC25N030ATDA04-0, DA4OA76A, max UDMA/100
[    2.944620] ata1.00: 58605120 sectors, multi 16: LBA 
[    2.960547] ata1.00: configured for UDMA/100
[    3.124397] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2002, 1W26, max MWDMA2
[    3.140377] ata2.00: configured for MWDMA2
[    3.141379] scsi 0:0:0:0: Direct-Access     ATA      IC25N030ATDA04-0 DA4O PQ: 0 ANSI: 5
[    3.141662] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[    3.141710] sd 0:0:0:0: [sda] Write Protect is off
[    3.141716] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.141788] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.141972] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[    3.142013] sd 0:0:0:0: [sda] Write Protect is off
[    3.142019] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.142087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.142099]  sda: sda1 sda3 < sda5 sda6 >
[    3.203051] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.203202] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.204885] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2002 1W26 PQ: 0 ANSI: 5
[    3.212210] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.212218] Uniform CD-ROM driver Revision: 3.20
[    3.212514] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.212633] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.214177] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.214226] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.214263] uhci_hcd: USB Universal Host Controller Interface driver
[    3.215248] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.215260] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.215280] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.215288] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.215477] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.215523] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000cf80
[    3.215784] usb usb1: configuration #1 chosen from 1 choice
[    3.215853] hub 1-0:1.0: USB hub found
[    3.215880] hub 1-0:1.0: 2 ports detected
[    3.216988] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.216999] uhci_hcd 0000:00:1f.4: PCI INT C -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.217016] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    3.217023] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    3.217146] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    3.217183] uhci_hcd 0000:00:1f.4: irq 11, io base 0x0000cf60
[    3.217403] usb usb2: configuration #1 chosen from 1 choice
[    3.217469] hub 2-0:1.0: USB hub found
[    3.217495] hub 2-0:1.0: 2 ports detected
[    3.217796] usbcore: registered new interface driver libusual
[    3.217894] usbcore: registered new interface driver usbserial
[    3.217921] USB Serial support registered for generic
[    3.217954] usbcore: registered new interface driver usbserial_generic
[    3.217960] usbserial: USB Serial Driver core
[    3.218073] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.224280] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.224297] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.224577] mice: PS/2 mouse device common for all mice
[    3.224891] rtc_cmos 00:07: RTC can wake from S4
[    3.224987] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.225016] rtc0: alarms up to one year, 114 bytes nvram
[    3.225257] device-mapper: uevent: version 1.0.3
[    3.225593] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.225748] device-mapper: multipath: version 1.0.5 loaded
[    3.225756] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.226019] EISA: Probing bus 0 at eisa.0
[    3.226034] Cannot allocate resource for EISA slot 1
[    3.226062] EISA: Detected 0 cards.
[    3.226238] cpuidle: using governor ladder
[    3.226341] cpuidle: using governor menu
[    3.227748] TCP cubic registered
[    3.228085] NET: Registered protocol family 10
[    3.229195] lo: Disabled Privacy Extensions
[    3.230013] NET: Registered protocol family 17
[    3.230071] Bluetooth: L2CAP ver 2.11
[    3.230076] Bluetooth: L2CAP socket layer initialized
[    3.230084] Bluetooth: SCO (Voice Link) ver 0.6
[    3.230088] Bluetooth: SCO socket layer initialized
[    3.230237] Bluetooth: RFCOMM socket layer initialized
[    3.230261] Bluetooth: RFCOMM TTY layer initialized
[    3.230266] Bluetooth: RFCOMM ver 1.10
[    3.230403] IO APIC resources could be not be allocated.
[    3.230422] Using IPI No-Shortcut mode
[    3.230737] registered taskstats version 1
[    3.231021]   Magic number: 9:122:299
[    3.231204] rtc_cmos 00:07: setting system clock to 2009-05-01 22:17:42 UTC (1241216262)
[    3.231212] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.231217] EDD information not available.
[    3.233689] Freeing unused kernel memory: 532k freed
[    3.234028] Write protecting the kernel text: 4128k
[    3.234119] Write protecting the kernel read-only data: 1532k
[    3.243923] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.464803] vesafb: framebuffer at 0xfc000000, mapped to 0xe0800000, using 3072k, total 16384k
[    3.464815] vesafb: mode is 1024x768x16, linelength=2048, pages=9
[    3.464820] vesafb: protected mode interface info at c000:7722
[    3.464826] vesafb: pmi: set display start = c00c7743, set palette = c00c77a6
[    3.464831] vesafb: scrolling: redraw
[    3.464837] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    3.465121] Console: switching to colour frame buffer device 128x48
[    3.497694] fb0: VESA VGA frame buffer device
[    3.552110] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.724115] usb 1-1: configuration #1 chosen from 1 choice
[    3.728425] hub 1-1:1.0: USB hub found
[    3.732884] hub 1-1:1.0: 4 ports detected
[    4.005972] Floppy drive(s): fd0 is 1.44M
[    4.022336] FDC 0 is a post-1991 82077
[    4.073235] usb 1-1.3: new low speed USB device using uhci_hcd and address 3
[    4.135623] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    4.135633] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.136335] e100 0000:02:08.0: power state changed by ACPI to D0
[    4.137085] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    4.137096] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    4.160202] e100 0000:02:08.0: PME# disabled
[    4.184544] e100: eth0: e100_probe: addr 0xf7dff000, irq 11, MAC addr 00:00:39:8d:b4:2c
[    4.235848] usb 1-1.3: configuration #1 chosen from 1 choice
[    5.203946] usbcore: registered new interface driver hiddev
[    5.236626] input: Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[    5.237714] generic-usb 0003:045E:00D2.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel] on usb-0000:00:1f.2-1.3/input0
[    5.237773] usbcore: registered new interface driver usbhid
[    5.237783] usbhid: v2.6:USB HID core driver
[    5.257526] Marking TSC unstable due to TSC halts in idle
[    5.378973] PM: Starting manual resume from disk
[    5.378987] PM: Resume from partition 8:6
[    5.378991] PM: Checking hibernation image.
[    5.379369] PM: Resume from disk failed.
[    5.438826] kjournald starting.  Commit interval 5 seconds
[    5.438867] EXT3-fs: mounted filesystem with ordered data mode.
[    5.476051] Clocksource tsc unstable (delta = -584722389 ns)
[   22.164903] udev: starting version 141
[   23.909424] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   24.183800] acpi device:1c: registered as cooling_device2
[   24.184613] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1a/device:1b/input/input6
[   24.207999] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   24.249220] parport_pc 00:0c: reported by Plug and Play ACPI
[   24.249288] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.322139] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.344657] Intel 82802 RNG detected
[   24.428398] Linux agpgart interface v0.103
[   24.477657] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   24.477667] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   24.479379] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   24.479389] toshiba_acpi: ktoshkeyd will check 2 times per second
[   24.480325] toshiba_acpi: Dropped 0 keys from the queue on startup
[   24.594241] ppdev: user-space parallel port driver
[   24.705078] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   24.854554] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[   24.859973] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf0000000
[   24.918735] yenta_cardbus 0000:02:0c.0: CardBus bridge found [12a3:ab01]
[   24.918770] yenta_cardbus 0000:02:0c.0: Using CSCINT to route CSC interrupts to PCI
[   24.918776] yenta_cardbus 0000:02:0c.0: Routing CardBus interrupts to PCI
[   24.918785] yenta_cardbus 0000:02:0c.0: TI: mfunc 0x01000002, devctl 0x62
[   24.934228] iTCO_vendor_support: vendor-support=0
[   24.939955] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   24.942547] iTCO_wdt: Found a ICH2-M TCO device (Version=1, TCOBASE=0xee60)
[   24.942756] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.020003] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.150365] yenta_cardbus 0000:02:0c.0: ISA IRQ mask 0x0000, PCI irq 11
[   25.150378] yenta_cardbus 0000:02:0c.0: Socket status: 30000059
[   25.150396] yenta_cardbus 0000:02:0c.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   25.150407] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xdfff: clean.
[   25.150866] yenta_cardbus 0000:02:0c.0: pcmcia: parent PCI bridge Memory window: 0xf7d00000 - 0xf7dfffff
[   25.150874] yenta_cardbus 0000:02:0c.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3bffffff
[   25.152366] yenta_cardbus 0000:02:0d.0: CardBus bridge found [1179:0001]
[   25.253584] psmouse serio1: ID: 12 02 64<6>yenta_cardbus 0000:02:0d.0: ISA IRQ mask 0x0438, PCI irq 11
[   25.282464] yenta_cardbus 0000:02:0d.0: Socket status: 30000007
[   25.282477] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #07 to #0a
[   25.314620] yenta_cardbus 0000:02:0d.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   25.314634] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xd000-0xdfff: clean.
[   25.315093] yenta_cardbus 0000:02:0d.0: pcmcia: parent PCI bridge Memory window: 0xf7d00000 - 0xf7dfffff
[   25.315101] yenta_cardbus 0000:02:0d.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3bffffff
[   25.316175] yenta_cardbus 0000:02:0d.1: CardBus bridge found [1179:0001]
[   25.327129] nf_conntrack version 0.5.0 (8182 buckets, 32728 max)
[   25.346825] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   25.346837] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   25.346843] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.448938] yenta_cardbus 0000:02:0d.1: ISA IRQ mask 0x0438, PCI irq 11
[   25.448952] yenta_cardbus 0000:02:0d.1: Socket status: 30000020
[   25.448963] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #0a to #0e
[   25.448987] yenta_cardbus 0000:02:0d.1: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   25.448999] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xd000-0xdfff: clean.
[   25.449460] yenta_cardbus 0000:02:0d.1: pcmcia: parent PCI bridge Memory window: 0xf7d00000 - 0xf7dfffff
[   25.449468] yenta_cardbus 0000:02:0d.1: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3bffffff
[   25.730520] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   25.730559] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   25.824262] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   25.840053] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf7d00000-0xf7dfffff: excluding 0xf7d00000-0xf7d0ffff 0xf7df0000-0xf7dfffff
[   25.848963] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   25.957874] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   26.192256] pcmcia_socket pcmcia_socket2: pccard: CardBus card inserted into slot 2
[   26.192322] pci 0000:0b:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[   26.300079] intel8x0_measure_ac97_clock: measured 55218 usecs
[   26.300090] intel8x0: clocking to 48000
[   26.450856] cfg80211: Using static regulatory domain info
[   26.450866] cfg80211: Regulatory domain: US
[   26.450871] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.450878] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   26.450884] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   26.450891] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   26.450897] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   26.450903] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   26.450909] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   26.451114] cfg80211: Calling CRDA for country: US
[   26.600862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   26.601916] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   26.602374] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.602796] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.603519] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.605772] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   26.606830] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   26.607289] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   26.607710] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   26.608511] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   26.610613] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x100-0x3af: clean.
[   26.611926] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x3e0-0x4ff: clean.
[   26.612440] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x820-0x8ff: clean.
[   26.612863] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xc00-0xcf7: clean.
[   26.613594] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xa00-0xaff: clean.
[   26.801957] cfg80211: Regulatory domain changed to country: US
[   26.801972] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.801979] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   26.801986] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   26.801992] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.801998] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.802004] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   26.843761] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   26.852610] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   26.939371] eth1: Hardware identity 0005:0002:0001:0002
[   26.939482] eth1: Station identity  001f:0001:0006:000e
[   26.939489] eth1: Firmware determined as Lucent/Agere 6.14
[   26.939500] eth1: Attempting to download firmware agere_sta_fw.bin
[   26.939525] hermes_dld: AUX enable returned 0
[   26.940459] hermes_dld: AUX disable returned 0
[   26.940464] hermes_dld: Actual PDA length 998, Max allowed 1000
[   26.940469] eth1: Read PDA returned 0
[   26.940477] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   26.954390] ath5k 0000:0b:00.0: enabling device (0000 -> 0002)
[   26.954418] ath5k 0000:0b:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   26.954720] ath5k 0000:0b:00.0: registered as 'phy0'
[   27.221762] eth1: Cannot find firmware agere_sta_fw.bin
[   27.221836] eth1: Hardware identity 0005:0002:0001:0002
[   27.221941] eth1: Station identity  001f:0001:0006:000e
[   27.221948] eth1: Firmware determined as Lucent/Agere 6.14
[   27.221953] eth1: Ad-hoc demo mode supported
[   27.221958] eth1: IEEE standard IBSS ad-hoc mode supported
[   27.221963] eth1: WEP supported, 104-bit key
[   27.222071] eth1: MAC address 00:02:2d:26:70:1c
[   27.222170] eth1: Station name "HERMES I"
[   27.222722] eth1: ready
[   27.224952] eth1: orinoco_cs at 0.0, irq 11, io 0xd100-0xd13f
[   27.227672] phy0: Selected rate control algorithm 'minstrel'
[   27.421405] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   27.492470] ath_hal: module license 'Proprietary' taints kernel.
[   27.500120] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[   27.734494] udev: renamed network interface wlan0 to ath0
[   28.015898] lp0: using parport0 (interrupt-driven).
[   28.476694] Adding 497972k swap on /dev/sda6.  Priority:-1 extents:1 across:497972k
[   29.219868] EXT3 FS on sda5, internal journal
[   31.482469] type=1505 audit(1241230690.748:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2135
[   31.642351] type=1505 audit(1241230690.908:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2139
[   31.643100] type=1505 audit(1241230690.908:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2139
[   31.643449] type=1505 audit(1241230690.908:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2139
[   31.643683] type=1505 audit(1241230690.908:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2139
[   32.081592] type=1505 audit(1241230691.348:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2144
[   32.082661] type=1505 audit(1241230691.348:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2144
[   32.225744] type=1505 audit(1241230691.492:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2148
[   32.326805] type=1505 audit(1241230691.592:10): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2152
[   32.419924] type=1505 audit(1241230691.684:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2156
[   61.476979] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   61.476988] Bluetooth: BNEP filters: protocol multicast
[   61.568830] Bridge firewalling registered
[   67.753294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.756193] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   67.876499] ADDRCONF(NETDEV_UP): ath0: link is not ready
[   67.887997] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   67.888986] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   67.919466] eth1: New link status: Disconnected (0002)
[  514.769045] ath0: authenticate with AP df8e96b8
[  514.771180] ath0: authenticated
[  514.771190] ath0: associate with AP df8e96b8
[  514.773631] ath0: RX AssocResp from de5d308a (capab=0x431 status=0 aid=1)
[  514.773643] ath0: associated
[  514.777363] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  514.866838] cfg80211: Calling CRDA for country: US
[  514.876810] cfg80211: Current regulatory domain updated by AP to: US
[  514.876825] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  514.876835] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  525.392064] ath0: no IPv6 routers present
[  560.950943] ath0: disassociating by local choice (reason=3)
[ 1004.000352] e100: eth0: e100_watchdog: link down
[ 1018.022297] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 4455.986603] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 4455.986615] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 4455.986623] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 4455.988332] pcmcia_socket pcmcia_socket2: cs: memory probe 0xf7d00000-0xf7dfffff: excluding 0xf7d00000-0xf7d1ffff 0xf7df0000-0xf7dfffff
hoe1@hoe1-laptop:~$

---

### Post by t0mppa on 2009-05-02
> **iClouseau88 said:**
> I am wondering why ath5k (Madwifi) driver is present but not shown in System>Admin>Hardware Drivers:

Ath5k comes in Jaunty as default, the Atheros driver in Hardware Drivers is the original MadWifi driver, which you shouldn't need, since ath5k appears to work. Looks like IPv6 might be the culprit here, since on dmesg it appears to connect with your AP just fine, but then disconnect afterwards, when no IPv6 routers are found.

[See here]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html") on how to disable it.

---

### Post by iClouseau88 on 2009-05-02
Hi,

I followed the link you gave in the above post and disabled IPv6 which came as default in Jaunty.  After rebooting,I temporarily unplugged the Cat5 cable but found no wireless connection for my machine.  System>Admin>Hardware Driver shows original madwifi driver (ath5k) again but it was greyed out and I had to push "Activate".  Still no wireless.  There is a symbol with 2 blue arrows in opposite directions and a note explaining that ath5k was disabled but still in use.  I never disabled ath5k because I made it to work in Intrepid.  I read somewhere that Ubuntu disabled it in Jaunty.  This is frustrating for newbies like myself; I don't understand why Ubuntu people tend to mess up wireless drivers in each new distribution.  If something works, then leave it alone!

Help!!!!

---

### Post by iClouseau88 on 2009-05-02
hoe1@hoe1-laptop:~$ dmesg|grep ath5k
[   27.124453] ath5k 0000:0b:00.0: enabling device (0000 -> 0002)
[   27.124483] ath5k 0000:0b:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   27.124809] ath5k 0000:0b:00.0: registered as 'phy0'
[   27.565393] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)

Any suggestion?

---

### Post by t0mppa on 2009-05-02
Mind posting some results from the terminal again, to see what's up now? Mainly ```
ifconfig
iwlist scan
lsmod
```

---

### Post by AnthraxMouthwash on 2009-05-02
Bump.

I have almost the same problem as this.

I updated my Ubuntu Hardy to Intrepid and everything worked perfectly still.  Absolutely nothing was broken.

Shortly after, I proceeded with the Jaunty update.  After restart, a lot of things were broken.  The most disasterous is this wireless issue.

I have spent many hours trying to resolve this now.  I have read a lot of posts saying this is an IPv6 issue -- it is not.

I entered all the info (ESSID, pass key, etc) to connect to my router, but not only is it not connecting but I am seeing ZERO ACTIVITY from my wifi device.

I have an Edimax EW-7318USg USB wifi stick.  I was working 100% fine out-of-the-box under Hardy and Intrepid.  It still works 100% under Windows 2000 (also on the same machine).

In Jaunty, the EW-7318USg is, as I said, brick-dead and makes no attempt at activity at any time, which is why I suggest it is not an IPv6 issue.  It seems the RT72/RT2500 driver is broken in Jaunty.

I can not get that NDisWrapper thing to take the windows drivers.  RT2500.inf from Win2k, XP, 9X, fail to do anything, and the driver status says the device is not present.  RT72.inf from any of those Windows versions show a dialogue saying "could not determine if device is present" and defaults to saying the device IS present, but still does not work even after reboot.

All of that is academic, though.  I should not HAVE to use the windows drivers.  Hardy and Intrepid worked fine.  I fervently agree with this comment:

> If something works, then leave it alone!



Anyone have any other advice?  I really need Ubuntu working with net connection.  I would prefer not to have to re-install from scratch with Intrepid, which is beginning to seem like my only option.

Oh, and please remember that the advice needs to be feesible to do without a web connection in Ubuntu.  Downloading packages with a lot of dependencies is tricky to do manually.  As most of us are probably aware... :)

Thanks in advance.

---

### Post by womblet on 2009-05-02
I also have the same problem with Jaunty (on a Dell Latitude). I think my problem may have stemmed from having my wireless switch off during the install.

---

### Post by iClouseau88 on 2009-05-02
1)output of ifconfig:

hoe1@hoe1-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:d9:d1:f0  
          inet6 addr: fe80::215:e9ff:fed9:d1f0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:312 (312.0 B)  TX bytes:3380 (3.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:00:39:8d:b4:2c  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe8d:b42c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1262844 (1.2 MB)  TX bytes:189720 (189.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:26:70:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-D9-D1-F0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

2) output of iwlist scan:

hoe1@hoe1-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

wmaster0  Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:D1:50:8C:F6
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"snynhatrang"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000261ab02458
                    Extra: Last beacon: 247164ms ago
                    IE: Unknown: 000B736E796E68617472616E67
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101070003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F

pan0      Interface doesn't support scanning.

3) output of lsmod:

hoe1@hoe1-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
ath_pci               217784  0 
wlan                  238064  1 ath_pci
ath_hal               312160  1 ath_pci
arc4                    9856  2 
ecb                    10752  2 
orinoco_cs             21004  1 
orinoco                61716  1 orinoco_cs
ath5k                 126724  0 
hermes_dld             15232  1 orinoco
lbm_cw_mac80211       227364  1 ath5k
lbm_cw_cfg80211        73760  2 ath5k,lbm_cw_mac80211
led_class              12036  1 ath5k
hermes                 15360  3 orinoco_cs,orinoco,hermes_dld
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
iptable_mangle         10880  0 
snd_intel8x0           37532  3 
iptable_filter         10752  0 
pcmcia                 44748  1 orinoco_cs
snd_ac97_codec        112292  1 snd_intel8x0
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
ac97_bus                9856  1 snd_ac97_codec
x_tables               23044  2 iptable_nat,ip_tables
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
ppdev                  15620  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
yenta_socket           32396  6 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             40100  1 
psmouse                61972  0 
intel_agp              34108  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
toshiba_acpi           18624  0 
input_polldev          11912  1 toshiba_acpi
parport                42220  3 lp,ppdev,parport_pc
video                  25360  0 
serio_raw              13316  0 
agpgart                42696  1 intel_agp
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
output                 11008  1 video
shpchp                 40212  0 
usbhid                 42336  0 
e100                   41740  0 
mii                    13312  1 e100
floppy                 64324  0 
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by gtstephenson on 2009-05-02
I had the same symptom. I have the thing fixed now. Went to System -> Admin -> hardware drivers. Found the "Alternate Athros madwifi" driver in the list and that it was disabled. The text indicated that there was a driver that should work but if it didn't to enable the madwifi driver.

Authentication didn't work. So then I went to the Authentication tab and enabled the console to have authorization for driver install. Went back to the network driver and enabled the madwifi driver. After that everything came up.

Best of luck to you,

Tom Stephenson

---

### Post by iClouseau88 on 2009-05-03
How did you enable the console to authorize driver  installation?  Because when I hit the"Authenticate" button I still don't get wireless connection.

Thanks in advance.

---

### Post by SabreWolfy on 2009-05-04
I think it's an issue in Jaunty, certainly for wired connections (see thread [here]("http://ubuntuforums.org/showthread.php?p=7212852") and bug report [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368709")).

---

### Post by Muriluo on 2009-05-12
Hi! I have the same problem... Actually it looks worse.

After I uploaded Jaunty my wireless just vanished as it had never existed.  I went on Win Vista and the same! No sign of my built in wireless card in Jaunty nor in Vista.

I decided to, temporarily use a USB wireless card (Enuwi-g). I did the ndiswrapper and rebooted Jaunty. The built in card was working as nothing had happened. So I went to Vista and the wireless card was now showing up there... I went back to jaunty and again, it had vanished from my computer as nothing had happened.

In the end, the USB wifi did not work on Jaunty 64bits. I went to Vista and tried to install the USB card. Rebooted my system and there was my built in wireless working perfectly! I used it for a long time till Vista ask to reboot because I was installing some softwares. When it loaded, no sign of the built in!

Conclusion: after jaunty update my built in wi-fi vanished and it worked back when I tried to install another wireless card, but as soon as I restarted my computer, it had vanished again! Now, no sign of it! Any help?

---

### Post by Muriluo on 2009-05-12
here are the commands I did to test it:

[http://ubuntuforums.org/showthread.php?t=1133737](http://ubuntuforums.org/showthread.php?t=1133737)

---

### Post by bungee_70 on 2009-05-12
Hi, I experience the exact same error as iClouseau88: I have an Atheros AR5004X on WPA. I think eiher the Atheros or the WPA is the problem...

I can't either activate Madwifi, same symptom as iClouseau88.

Any idea?

---

### Post by mspaul on 2009-07-18
Arggggggggg  jaunty64 here 

Vista wifi worked great, until I installed Wubi Jaunty and now vista wifi wont connect

it is detected however

I have a rtl8187b on-board wifi on a gateway laptop

---

### Post by mspaul on 2009-07-18
unticking enable wireless box on the network applet before a reboot into vista fixes the problem for me

I may try ndiswapper to see if that works too

---

