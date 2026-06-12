---
title: "/etc/network/interfaces and dhcp/static IP"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by Carbonwyre on 2012-12-07
I have a server set up on my computer, it is fully functional at least on my connection but it doesn't have a proper static ipv4 (right now it's just the 10.0.x.x)and I'm looking for the longer proper one if that makes sense.

At the moment in my interfaces file all I have is

auto lo
iface lo lnet loopback

but I don't have

auto eth0
iface eth0 lnet dhcp (or static)

How do I fix this? Or at least get to my destination of being able to access this server from other connections then my local one?

---

### Post by TheFu on 2012-12-07
What do the logs and **dmesg **say?
Is the network hardware recognized at all?  [B]sudo lshw -c network
[/B]Is the driver for your NIC loading? **lsmod** 

If no network card is seen, there isn't any reason for interfaces to include any non-loopback devices.

---

### Post by Carbonwyre on 2012-12-07
I still have a little of a hard time understanding it all
I am fully connected to the Internet, but I am using an Ethernet cord to do it.
The main question is how do I get from where I am now to having a static IP I can connect to from anywhere

dmesg
> [    0.132118] vgaarb: loaded
[    0.132120] vgaarb: bridge control possible 0000:00:02.0
[    0.132361] SCSI subsystem initialized
[    0.132444] libata version 3.00 loaded.
[    0.132477] ACPI: bus type usb registered
[    0.132501] usbcore: registered new interface driver usbfs
[    0.132513] usbcore: registered new interface driver hub
[    0.132545] usbcore: registered new device driver usb
[    0.132660] PCI: Using ACPI for IRQ routing
[    0.139574] PCI: pci_cache_line_size set to 64 bytes
[    0.139657] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.139661] e820: reserve RAM buffer [mem 0x7f7f0000-0x7fffffff]
[    0.139845] NetLabel: Initializing
[    0.139848] NetLabel:  domain hash size = 128
[    0.139850] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.139865] NetLabel:  unlabeled traffic allowed by default
[    0.140101] hpet clockevent registered
[    0.140105] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.140110] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.140116] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.144238] Switching to clocksource hpet
[    0.154593] AppArmor: AppArmor Filesystem Enabled
[    0.154638] pnp: PnP ACPI init
[    0.154661] ACPI: bus type pnp registered
[    0.154783] pnp 00:00: [bus 00-ff]
[    0.154787] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.154791] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.154793] pnp 00:00: [io  0x0d00-0xffff window]
[    0.154797] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.154799] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.154802] pnp 00:00: [mem 0x7f800000-0xfebfffff window]
[    0.154887] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.154955] pnp 00:01: [io  0x0010-0x001f]
[    0.154958] pnp 00:01: [io  0x0022-0x003f]
[    0.154960] pnp 00:01: [io  0x0044-0x005f]
[    0.154963] pnp 00:01: [io  0x0062-0x0063]
[    0.154965] pnp 00:01: [io  0x0065-0x006f]
[    0.154968] pnp 00:01: [io  0x0074-0x007f]
[    0.154970] pnp 00:01: [io  0x0091-0x0093]
[    0.154973] pnp 00:01: [io  0x00a2-0x00bf]
[    0.154975] pnp 00:01: [io  0x00e0-0x00ef]
[    0.154978] pnp 00:01: [io  0x04d0-0x04d1]
[    0.154980] pnp 00:01: [io  0x0290-0x029f]
[    0.154983] pnp 00:01: [io  0x0800-0x087f]
[    0.154985] pnp 00:01: [io  0x0880-0x088f]
[    0.155051] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.155055] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.155058] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.155061] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.155066] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.155083] pnp 00:02: [dma 4]
[    0.155086] pnp 00:02: [io  0x0000-0x000f]
[    0.155089] pnp 00:02: [io  0x0080-0x0090]
[    0.155091] pnp 00:02: [io  0x0094-0x009f]
[    0.155094] pnp 00:02: [io  0x00c0-0x00df]
[    0.155127] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.155140] pnp 00:03: [io  0x0070-0x0073]
[    0.155155] pnp 00:03: [irq 8]
[    0.155185] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.155195] pnp 00:04: [io  0x0061]
[    0.155237] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.155248] pnp 00:05: [io  0x00f0-0x00ff]
[    0.155259] pnp 00:05: [irq 13]
[    0.155290] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.155588] pnp 00:06: [io  0x03f8-0x03ff]
[    0.155597] pnp 00:06: [irq 4]
[    0.155672] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.155893] pnp 00:07: [io  0x02f8-0x02ff]
[    0.155900] pnp 00:07: [irq 3]
[    0.155977] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.156303] pnp 00:08: [io  0x0378-0x037f]
[    0.156312] pnp 00:08: [irq 7]
[    0.156371] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.156487] pnp 00:09: [io  0x0060]
[    0.156490] pnp 00:09: [io  0x0064]
[    0.156497] pnp 00:09: [irq 1]
[    0.156537] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.156575] pnp 00:0a: [io  0x0400-0x04bf]
[    0.156633] system 00:0a: [io  0x0400-0x04bf] has been reserved
[    0.156638] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.156660] pnp 00:0b: [mem 0xffb80000-0xffbfffff]
[    0.156699] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.156915] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.156990] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.156994] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.157146] pnp 00:0d: [mem 0x000cc000-0x000cffff]
[    0.157150] pnp 00:0d: [mem 0x000d5000-0x000d7fff]
[    0.157152] pnp 00:0d: [mem 0x000f0000-0x000fbfff]
[    0.157155] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.157158] pnp 00:0d: [mem 0x7f7f0000-0x7f7fffff]
[    0.157160] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.157163] pnp 00:0d: [mem 0x00100000-0x7f7effff]
[    0.157169] pnp 00:0d: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.157172] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.157174] pnp 00:0d: [mem 0xfed13000-0xfed1dfff]
[    0.157177] pnp 00:0d: [mem 0xfed20000-0xfed8ffff]
[    0.157179] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.157182] pnp 00:0d: [mem 0xffb00000-0xffb7ffff]
[    0.157185] pnp 00:0d: [mem 0xfff00000-0xffffffff]
[    0.157187] pnp 00:0d: [mem 0x000e0000-0x000effff]
[    0.157263] system 00:0d: [mem 0x000cc000-0x000cffff] has been reserved
[    0.157267] system 00:0d: [mem 0x000d5000-0x000d7fff] has been reserved
[    0.157270] system 00:0d: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.157274] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.157277] system 00:0d: [mem 0x7f7f0000-0x7f7fffff] could not be reserved
[    0.157280] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.157284] system 00:0d: [mem 0x00100000-0x7f7effff] could not be reserved
[    0.157287] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.157290] system 00:0d: [mem 0xfed13000-0xfed1dfff] has been reserved
[    0.157293] system 00:0d: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.157297] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.157300] system 00:0d: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.157303] system 00:0d: [mem 0xfff00000-0xffffffff] has been reserved
[    0.157306] system 00:0d: [mem 0x000e0000-0x000effff] has been reserved
[    0.157311] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.157323] pnp: PnP ACPI: found 14 devices
[    0.157326] ACPI: ACPI bus type pnp unregistered
[    0.163938] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.163948] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.163954] pci 0000:00:1e.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.163959] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.163976] pci 0000:00:1e.0: setting latency timer to 64
[    0.163981] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.163984] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.163987] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.163990] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.163993] pci_bus 0000:01: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.163996] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.163999] pci_bus 0000:01: resource 5 [mem 0x00000000-0xfffffffff]
[    0.164087] NET: Registered protocol family 2
[    0.164219] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.164970] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.167824] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.168493] TCP: Hash tables configured (established 262144 bind 65536)
[    0.168499] TCP: reno registered
[    0.168519] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.168543] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.168704] NET: Registered protocol family 1
[    0.168732] pci 0000:00:02.0: Boot video device
[    0.168913] PCI: CLS 32 bytes, default 64
[    0.169415] audit: initializing netlink socket (disabled)
[    0.169429] type=2000 audit(1354888821.168:1): initialized
[    0.196598] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.198848] VFS: Disk quotas dquot_6.5.2
[    0.198908] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.199585] fuse init (API version 7.19)
[    0.199688] msgmni has been set to 3954
[    0.200142] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.200183] io scheduler noop registered
[    0.200185] io scheduler deadline registered (default)
[    0.200223] io scheduler cfq registered
[    0.200358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.200383] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.200452] intel_idle: does not run on family 6 model 15
[    0.200543] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.200549] ACPI: Power Button [PWRB]
[    0.200613] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.200617] ACPI: Power Button [PWRF]
[    0.200675] ACPI: Fan [FAN] (on)
[    0.200750] ACPI: Requesting acpi_cpufreq
[    0.440380] Freeing initrd memory: 14872k freed
[    0.451502] thermal LNXTHERM:00: registered as thermal_zone0
[    0.451507] ACPI: Thermal Zone [THRM] (40 C)
[    0.451546] GHES: HEST is not enabled!
[    0.451689] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.472094] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.492515] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.514054] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.534516] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.534760] Linux agpgart interface v0.103
[    0.534826] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    0.534896] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.535179] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.535317] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.537067] brd: module loaded
[    0.538010] loop: module loaded
[    0.538178] ata_piix 0000:00:1f.1: version 2.13
[    0.538233] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.538607] scsi0 : ata_piix
[    0.538712] scsi1 : ata_piix
[    0.539195] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    0.539199] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    0.539227] ata_piix 0000:00:1f.2: MAP [
[    0.539229]  P0 P2 P1 P3 ]
[    0.539276] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.539285] ata2: port disabled--ignoring
[    0.539678] scsi2 : ata_piix
[    0.539765] scsi3 : ata_piix
[    0.540267] ata3: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    0.540270] ata4: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    0.540636] Fixed MDIO Bus: probed
[    0.540690] tun: Universal TUN/TAP device driver, 1.6
[    0.540691] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.540810] PPP generic driver version 2.4.2
[    0.540875] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.540927] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.540931] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.540939] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.540961] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.544854] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.544876] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.556032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.556073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.556078] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.556082] usb usb1: Product: EHCI Host Controller
[    0.556087] usb usb1: Manufacturer: Linux 3.5.0-19-generic ehci_hcd
[    0.556091] usb usb1: SerialNumber: 0000:00:1d.7
[    0.556282] hub 1-0:1.0: USB hub found
[    0.556288] hub 1-0:1.0: 8 ports detected
[    0.556376] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.556397] uhci_hcd: USB Universal Host Controller Interface driver
[    0.556426] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.556430] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.556442] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.556467] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    0.556503] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.556506] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.556509] usb usb2: Product: UHCI Host Controller
[    0.556512] usb usb2: Manufacturer: Linux 3.5.0-19-generic uhci_hcd
[    0.556515] usb usb2: SerialNumber: 0000:00:1d.0
[    0.556626] hub 2-0:1.0: USB hub found
[    0.556631] hub 2-0:1.0: 2 ports detected
[    0.556705] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.556709] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.556715] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.556741] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    0.556779] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.556782] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.556785] usb usb3: Product: UHCI Host Controller
[    0.556788] usb usb3: Manufacturer: Linux 3.5.0-19-generic uhci_hcd
[    0.556791] usb usb3: SerialNumber: 0000:00:1d.1
[    0.556895] hub 3-0:1.0: USB hub found
[    0.556900] hub 3-0:1.0: 2 ports detected
[    0.556973] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.556977] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.556984] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.557017] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    0.557052] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.557056] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.557059] usb usb4: Product: UHCI Host Controller
[    0.557061] usb usb4: Manufacturer: Linux 3.5.0-19-generic uhci_hcd
[    0.557064] usb usb4: SerialNumber: 0000:00:1d.2
[    0.557170] hub 4-0:1.0: USB hub found
[    0.557175] hub 4-0:1.0: 2 ports detected
[    0.557247] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.557251] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.557257] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.557292] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    0.557328] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.557331] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.557334] usb usb5: Product: UHCI Host Controller
[    0.557337] usb usb5: Manufacturer: Linux 3.5.0-19-generic uhci_hcd
[    0.557340] usb usb5: SerialNumber: 0000:00:1d.3
[    0.557448] hub 5-0:1.0: USB hub found
[    0.557453] hub 5-0:1.0: 2 ports detected
[    0.557580] usbcore: registered new interface driver libusual
[    0.557621] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.557623] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.558416] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.558540] mousedev: PS/2 mouse device common for all mice
[    0.558701] rtc_cmos 00:03: RTC can wake from S4
[    0.558830] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.558855] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.558955] device-mapper: uevent: version 1.0.3
[    0.559033] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.559042] cpuidle: using governor ladder
[    0.559044] cpuidle: using governor menu
[    0.559047] EFI Variables Facility v0.08 2004-May-17
[    0.559308] ashmem: initialized
[    0.559447] TCP: cubic registered
[    0.559574] NET: Registered protocol family 10
[    0.559823] NET: Registered protocol family 17
[    0.559835] Key type dns_resolver registered
[    0.559998] PM: Hibernation image not present or could not be loaded.
[    0.560028] registered taskstats version 1
[    0.563007] Key type trusted registered
[    0.565672] Key type encrypted registered
[    0.568649]   Magic number: 8:9:30
[    0.568780] rtc_cmos 00:03: setting system clock to 2012-12-07 14:00:22 UTC (1354888822)
[    0.569557] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.569560] EDD information not available.
[    0.581415] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.707122] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H40N, RG01, max UDMA/66
[    0.712346] ata3.00: ATA-7: Hitachi HDT725040VLA360, V5COA7EA, max UDMA/133
[    0.712350] ata3.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.720236] ata1.00: configured for UDMA/66
[    0.726199] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H40N  RG01 PQ: 0 ANSI: 5
[    0.728382] ata3.00: configured for UDMA/133
[    0.731950] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.731954] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.732147] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.732276] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.732453] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72504 V5CO PQ: 0 ANSI: 5
[    0.732583] sd 2:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    0.732611] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.732643] sd 2:0:0:0: [sda] Write Protect is off
[    0.732647] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.732694] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.765668]  sda: sda1 sda2 < sda5 >
[    0.766144] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.767716] Freeing unused kernel memory: 928k freed
[    0.768054] Write protecting the kernel read-only data: 12288k
[    0.773362] Freeing unused kernel memory: 1464k freed
[    0.777920] Freeing unused kernel memory: 1120k freed
[    0.801933] udevd[98]: starting version 175
[    0.906521] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.906554] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.907089] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.907845] 8139too 0000:01:05.0: eth0: RealTek RTL8139 at 0x000000000001ec00, 00:1b:b9:7f:4b:cd, IRQ 20
[    0.924099] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.057945] usb 1-8: New USB device found, idVendor=058f, idProduct=6377
[    1.057954] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.057959] usb 1-8: Product: Mass Storage Device
[    1.057963] usb 1-8: Manufacturer: Generic
[    1.057967] usb 1-8: SerialNumber: 920321111113
[    1.061058] Initializing USB Mass Storage driver...
[    1.061222] scsi4 : usb-storage 1-8:1.0
[    1.061331] usbcore: registered new interface driver usb-storage
[    1.061334] USB Mass Storage support registered.
[    1.061723] usbcore: registered new interface driver uas
[    1.168045] Refined TSC clocksource calibration: 1799.795 MHz.
[    1.168053] Switching to clocksource tsc
[    1.296102] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.464540] usb 2-1: New USB device found, idVendor=0461, idProduct=4d16
[    1.464546] usb 2-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.464551] usb 2-1: Product: USB Optical Mouse
[    1.483649] usbcore: registered new interface driver usbhid
[    1.483655] usbhid: USB HID core driver
[    1.486413] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.486583] hid-generic 0003:0461:4D16.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    1.687139] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.687146] EXT4-fs (sda1): write access will be enabled during recovery
[    2.061002] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.061716] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.062368] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.062992] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.064065] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.064322] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    2.067021] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    2.067266] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    2.074757] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.076375] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    2.076986] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    2.082431] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    3.391099] EXT4-fs (sda1): recovery complete
[    3.397616] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.169103] Adding 2086908k swap on /dev/sda5.  Priority:-1 extents:1 across:2086908k 
[    6.017053] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.320054] udevd[335]: starting version 175
[    7.353234] lp: driver loaded but no devices found
[    7.611113] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.757757] parport_pc 00:08: reported by Plug and Play ACPI
[    7.757806] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.852626] lp0: using parport0 (interrupt-driven).
[    7.935348] intel_rng: FWH not detected
[    8.094796] ppdev: user-space parallel port driver
[    8.102391] ACPI Warning: 0x0000000000000430-0x0000000000000433 SystemIO conflicts with Region \SPEN 1 (20120320/utaddress-251)
[    8.102402] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.102405] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    8.102408] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PM2S 1 (20120320/utaddress-251)
[    8.102414] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.102417] ACPI Warning: 0x0000000000000480-0x00000000000004bf SystemIO conflicts with Region \GPO2 1 (20120320/utaddress-251)
[    8.102422] ACPI Warning: 0x0000000000000480-0x00000000000004bf SystemIO conflicts with Region \GPB_ 2 (20120320/utaddress-251)
[    8.102427] ACPI Warning: 0x0000000000000480-0x00000000000004bf SystemIO conflicts with Region \GPO_ 3 (20120320/utaddress-251)
[    8.102432] ACPI Warning: 0x0000000000000480-0x00000000000004bf SystemIO conflicts with Region \PALD 4 (20120320/utaddress-251)
[    8.102437] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.102439] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.196688] microcode: CPU0 sig=0x6f2, pf=0x1, revision=0x56
[    8.408473] leds_ss4200: no LED devices found
[    8.521399] [drm] Initialized drm 1.1.0 20060810
[    8.585609] coretemp coretemp.0: Using relative temperature scale!
[    8.585629] coretemp coretemp.0: Using relative temperature scale!
[    8.606514] microcode: CPU1 sig=0x6f2, pf=0x1, revision=0x56
[    8.608932] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.052107] i915 0000:00:02.0: setting latency timer to 64
[    9.085028] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.085034] [drm] Driver supports precise vblank timestamp query.
[    9.085724] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.133116] [drm] initialized overlay support
[    9.296411] fbcon: inteldrmfb (fb0) is primary device
[    9.296647] Console: switching to colour frame buffer device 128x48
[    9.296682] fb0: inteldrmfb frame buffer device
[    9.296684] drm: registered panic notifier
[    9.296696] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.628038] snd_hda_intel 0000:00:1b.0: irq 40 for MSI/MSI-X
[    9.758553] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    9.758770] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    9.758972] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    9.759149] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    9.759334] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.333057] type=1400 audit(1354888832.261:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=620 comm="apparmor_parser"
[   10.333241] type=1400 audit(1354888832.261:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=619 comm="apparmor_parser"
[   10.333760] type=1400 audit(1354888832.261:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=619 comm="apparmor_parser"
[   10.334052] type=1400 audit(1354888832.261:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=619 comm="apparmor_parser"
[   10.334078] type=1400 audit(1354888832.261:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=620 comm="apparmor_parser"
[   10.334371] type=1400 audit(1354888832.261:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=620 comm="apparmor_parser"
[   10.941547] init: failsafe main process (727) killed by TERM signal
[   12.659800] type=1400 audit(1354888834.589:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[   12.660468] type=1400 audit(1354888834.589:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=802 comm="apparmor_parser"
[   12.678435] Bluetooth: Core ver 2.16
[   12.678476] NET: Registered protocol family 31
[   12.678479] Bluetooth: HCI device and connection manager initialized
[   12.678482] Bluetooth: HCI socket layer initialized
[   12.678484] Bluetooth: L2CAP socket layer initialized
[   12.678491] Bluetooth: SCO socket layer initialized
[   12.820684] Bluetooth: RFCOMM TTY layer initialized
[   12.820693] Bluetooth: RFCOMM socket layer initialized
[   12.820695] Bluetooth: RFCOMM ver 1.11
[   13.153991] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.153996] Bluetooth: BNEP filters: protocol multicast
[   16.019695] 8139too 0000:01:05.0: eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   16.193406] type=1400 audit(1354888838.121:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=909 comm="apparmor_parser"
[   16.193656] type=1400 audit(1354888838.121:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=908 comm="apparmor_parser"
[   16.193835] type=1400 audit(1354888838.121:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=909 comm="apparmor_parser"
[   16.194073] type=1400 audit(1354888838.121:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=908 comm="apparmor_parser"
[   16.198172] type=1400 audit(1354888838.125:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=911 comm="apparmor_parser"
[   16.198699] type=1400 audit(1354888838.125:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=911 comm="apparmor_parser"
[   16.198989] type=1400 audit(1354888838.125:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=911 comm="apparmor_parser"
[   16.258832] type=1400 audit(1354888838.185:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=910 comm="apparmor_parser"
[   16.259300] type=1400 audit(1354888838.185:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=910 comm="apparmor_parser"
[   16.340293] type=1400 audit(1354888838.269:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=914 comm="apparmor_parser"
[   23.683095] init: plymouth-stop pre-start process (1359) terminated with status 1 
sudo lshw -c network

>   *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1b:b9:7f:4b:cd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.1.62 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
lsmod

> Module                  Size  Used by
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
i915                  520629  3 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         46784  1 i915
coretemp               13400  0 
snd_timer              29425  2 snd_pcm,snd_seq
drm                   275528  4 i915,drm_kms_helper
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              22803  0 
lpc_ich                17061  0 
ppdev                  17073  0 
serio_raw              13215  0 
soundcore              15047  1 snd
i2c_algo_bit           13413  1 i915
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
video                  19335  1 i915
parport_pc             32688  1 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 ppdev,parport_pc,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
usb_storage            48838  0 
uas                    17844  0 
8139too                31917  0 
8139cp                 27234  0 


---

### Post by dannyboy79 on 2012-12-07
to make it so ubuntu gets a static IP you can do it 1 of 2 ways, you can use your router and MAC address reservation such that the router will always assign the same IP address to a device based on it MAC address OR you can add a line to your /etc/network/interfaces file. Here's an example one, network and gateway need to match what your router's internal IP is. I gave 10.0.0.10 just as an example but you'll want to choose one that will never cause a conflict with devices that are DHCP

```
auto eth0
iface eth0 inet static
        address 10.0.0.10
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.1

```


Now, if you want to be able to access your web server from outside your local internet you'll need to foward ports in your router to the IP of the ubuntu server, if you want to access it via a fully qualified domain name, you'll have to use a service like dyndns

---

### Post by Carbonwyre on 2012-12-07
You sir are awesome, but Im going to leave this un solved till I can get it working XD How would I go about actually editing /etc/network/interfaces?'

Could I use
> sudo -s
sudo nano etc/network/interfaces
How would I identify the servers IP?

Take pity on me, I've only been at this for a day but I'm learning fast XD

---

### Post by dannyboy79 on 2012-12-08
yes you can use nano and you'll have to use sudo to edit the file since it;s owned by root. do you have a router? as I stated it may be easier to do MAC address reservation versus setting a static IP within the interfaces file. you can find out the IP of the server by issuing 

ifconfig

---

### Post by TheFu on 2012-12-08
> **Carbonwyre said:**
> You sir are awesome, but Im going to leave this un solved till I can get it working XD How would I go about actually editing /etc/network/interfaces?'

Could I use

How would I identify the servers IP?

Take pity on me, I've only been at this for a day but I'm learning fast XD

I think you need to read up about IPv4 networking a little before you start trying to setup static IPs on your network.  Normally, a network administrator would provide the 3 needed items for /etc/network/interfaces so you wouldn't harm anyone else.  On a home network, it is unlikely you will harm anything too seriously. About the worst thing that can happen is you choose the same IP address that someone else is using on the network and block that access.

None of this is hard, but an understand of it will pay off for the rest of your life.

If you just want to know what to type in, boot with DHCP enabled and post the output of $ **ifconfig eth0**.  From that, we can probably tell you all you need to type in.

BTW, only 3 lines per interface are required for 11.xx and earlier Ubuntu versions. With 12.04 and later releases, 4 lines are needed.

This would be a reasonable setup for a home router on 192.168.1.1. 
```
auto eth0
iface eth0 inet static
  address 192.168.1.99
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1

```
Many home routers use 192.168.0.1, which would mean a different subnet is used. If you didn't change the subnet data for every line above, the PC wouldn't be able to communicate at all (most likely).

Anyway, I hope this helps.  After changing anything in this file, be certain to restart networking on the box.
**sudo /etc/init.d/networking restart** is the command for that, though newer releases are pushing the **sudo restart networking** methods.

---

