---
title: "AWUS036H usb adapter will connect but will not surf internet."
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by jstthe01 on 2012-12-28
Hello  All!
                       I am  kinda new to linux but love it! I got a alfa AWUS036H usb dongle for x-mas with hopes being very high, In my town they offer free wifi to anyone that is in range of pickin it up so I was  hopeing with my new dongle I could, well I can and at a pretty high signal strength but sometimes it will surf web pages very slow and sometimes not at all. I'm useing Ubuntu 12.10 and have not had any other problems with it besides this, I got that specific dongle because all the posts I had read told me that it worked best with ubuntu out of the box. I was going to go to the realtek website and get the latest drivers but to my knowledge its already in the brand new linux kernal. So just to see if I got a bad device or something I left the usb dongle in the same place and loaded the drivers it came with on a argh! WINDOWS laptop and to my surprize it worked flawlessly! connected at same dbl rate if not more than the linux box did and internet surfing was really fast!
I refuse to go back to useing windows so any help would be greatly appreciated.

Thanks's in advance!  I have included the output of dmesg,lshe -C network,lsusb, and ifconfig

Output of lsusb
```

Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Output of lshw -C network
 ```

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: XX:XX:XX:XX:XX:XX
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-21-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:f6cff000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: XX:XX:XX:XX:XX:XX
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5755m-v3.32 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f6bf0000-f6bfffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1
       logical name: wlan1
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-21-generic firmware=N/A ip=192.168.2.11 link=yes multicast=yes wireless=IEEE 802.11bg

```

Output of ifconfig
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:XXX.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18760 (18.7 KB)  TX bytes:18760 (18.7 KB)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:XXX.XXX.X.XX  Bcast:XXX.XXX.X.XXX  Mask:255.255.255.0
          inet6 addr: XXXX::XXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:453248 (453.2 KB)  TX bytes:61441 (61.4 KB)

```

Output of dmesg
```

[    0.358386] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.358390] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.358397] pci 0000:00:1e.0:   bridge window [mem 0xf6a00000-0xf6afffff]
[    0.358403] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.358462] pci 0000:00:1e.0: setting latency timer to 64
[    0.358472] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.358487] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.358490] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.358493] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.358496] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.358499] pci_bus 0000:00: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.358501] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.358504] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.358507] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.358510] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.358513] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.358515] pci_bus 0000:00: resource 14 [mem 0xfeda7000-0xfedfffff]
[    0.358518] pci_bus 0000:00: resource 15 [mem 0xfee10000-0xff9fffff]
[    0.358521] pci_bus 0000:00: resource 16 [mem 0xffc00000-0xffdfffff]
[    0.358524] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.358527] pci_bus 0000:0b: resource 1 [mem 0x84000000-0x841fffff]
[    0.358530] pci_bus 0000:0b: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
[    0.358533] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.358535] pci_bus 0000:0c: resource 1 [mem 0xf6c00000-0xf6cfffff]
[    0.358538] pci_bus 0000:0c: resource 2 [mem 0x84400000-0x845fffff 64bit pref]
[    0.358541] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.358544] pci_bus 0000:09: resource 1 [mem 0xf6b00000-0xf6bfffff]
[    0.358547] pci_bus 0000:09: resource 2 [mem 0x84600000-0x847fffff 64bit pref]
[    0.358550] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.358553] pci_bus 0000:03: resource 1 [mem 0xf6a00000-0xf6afffff]
[    0.358555] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.358558] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.358561] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.358564] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.358566] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.358569] pci_bus 0000:03: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.358572] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.358575] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.358578] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.358581] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.358583] pci_bus 0000:03: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.358586] pci_bus 0000:03: resource 14 [mem 0xfeda7000-0xfedfffff]
[    0.358589] pci_bus 0000:03: resource 15 [mem 0xfee10000-0xff9fffff]
[    0.358592] pci_bus 0000:03: resource 16 [mem 0xffc00000-0xffdfffff]
[    0.358595] pci_bus 0000:04: resource 0 [io  0x5000-0x50ff]
[    0.358597] pci_bus 0000:04: resource 1 [io  0x5400-0x54ff]
[    0.358600] pci_bus 0000:04: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.358603] pci_bus 0000:04: resource 3 [mem 0x8c000000-0x8fffffff]
[    0.358647] NET: Registered protocol family 2
[    0.358717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.358899] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.359345] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.359587] TCP: Hash tables configured (established 131072 bind 65536)
[    0.359589] TCP: reno registered
[    0.359592] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.359602] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.359683] NET: Registered protocol family 1
[    0.359705] pci 0000:00:02.0: Boot video device
[    0.360059] PCI: CLS 64 bytes, default 64
[    0.360542] audit: initializing netlink socket (disabled)
[    0.360554] type=2000 audit(1356735139.360:1): initialized
[    0.384243] highmem bounce pool size: 64 pages
[    0.384257] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.386291] VFS: Disk quotas dquot_6.5.2
[    0.386348] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.386967] fuse init (API version 7.19)
[    0.387060] msgmni has been set to 1679
[    0.387413] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.387443] io scheduler noop registered
[    0.387446] io scheduler deadline registered (default)
[    0.387454] io scheduler cfq registered
[    0.387667] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.387814] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.387960] pcieport 0000:00:1c.5: irq 42 for MSI/MSI-X
[    0.388095] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.388119] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.388193] intel_idle: does not run on family 6 model 15
[    0.388321] ACPI: AC Adapter [AC] (on-line)
[    0.388401] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.388797] ACPI: Lid Switch [LID]
[    0.388842] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.388846] ACPI: Power Button [PBTN]
[    0.388891] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.388894] ACPI: Sleep Button [SBTN]
[    0.388976] ACPI: Requesting acpi_cpufreq
[    0.621789] Freeing initrd memory: 21092k freed
[    0.632660] Monitor-Mwait will be used to enter C-1 state
[    0.632674] Monitor-Mwait will be used to enter C-2 state
[    0.632685] Monitor-Mwait will be used to enter C-3 state
[    0.632694] Marking TSC unstable due to TSC halts in idle
[    0.632713] ACPI: acpi_idle registered with cpuidle
[    0.686114] thermal LNXTHERM:00: registered as thermal_zone0
[    0.686117] ACPI: Thermal Zone [THM] (28 C)
[    0.686152] ACPI: Battery Slot [BAT0] (battery present)
[    0.686162] ACPI: Battery Slot [BAT1] (battery absent)
[    0.686201] GHES: HEST is not enabled!
[    0.686440] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.706894] ACPI: Battery Slot [BAT0] (battery present)
[    0.706916] ACPI: Battery Slot [BAT1] (battery absent)
[    0.706932] isapnp: Scanning for PnP cards...
[    0.709012] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.730760] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.731012] Linux agpgart interface v0.103
[    0.731123] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.731169] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.731656] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.731776] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.733389] brd: module loaded
[    0.734193] loop: module loaded
[    0.734350] ata_piix 0000:00:1f.1: version 2.13
[    0.734400] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.736047] scsi0 : ata_piix
[    0.736122] scsi1 : ata_piix
[    0.738054] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.738057] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.738088] ata_piix 0000:00:1f.2: MAP [
[    0.738090]  P0 P2 P1 P3 ]
[    0.738297] ata2: port disabled--ignoring
[    0.892044] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.892565] scsi2 : ata_piix
[    0.892632] scsi3 : ata_piix
[    0.894463] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 18
[    0.894471] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 18
[    0.894835] Fixed MDIO Bus: probed
[    0.894889] tun: Universal TUN/TAP device driver, 1.6
[    0.894891] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.894952] PPP generic driver version 2.4.2
[    0.894998] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.895041] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.895045] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.895052] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.895083] ehci_hcd 0000:00:1a.7: debug port 1
[    0.898974] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.898991] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.900388] ata1.00: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-T10N, A104, max UDMA/33
[    0.908202] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.908224] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.908228] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.908231] usb usb1: Product: EHCI Host Controller
[    0.908233] usb usb1: Manufacturer: Linux 3.5.0-21-generic ehci_hcd
[    0.908236] usb usb1: SerialNumber: 0000:00:1a.7
[    0.908371] hub 1-0:1.0: USB hub found
[    0.908377] hub 1-0:1.0: 4 ports detected
[    0.908472] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.908476] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.908481] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.908509] ehci_hcd 0000:00:1d.7: debug port 1
[    0.912402] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.912420] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.916268] ata1.00: configured for UDMA/33
[    0.924023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.924039] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.924042] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.924045] usb usb2: Product: EHCI Host Controller
[    0.924048] usb usb2: Manufacturer: Linux 3.5.0-21-generic ehci_hcd
[    0.924050] usb usb2: SerialNumber: 0000:00:1d.7
[    0.924169] hub 2-0:1.0: USB hub found
[    0.924174] hub 2-0:1.0: 6 ports detected
[    0.924261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.924287] uhci_hcd: USB Universal Host Controller Interface driver
[    0.924311] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.924315] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.924321] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.924352] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.924389] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.924392] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.924395] usb usb3: Product: UHCI Host Controller
[    0.924397] usb usb3: Manufacturer: Linux 3.5.0-21-generic uhci_hcd
[    0.924400] usb usb3: SerialNumber: 0000:00:1a.0
[    0.924516] hub 3-0:1.0: USB hub found
[    0.924525] hub 3-0:1.0: 2 ports detected
[    0.924610] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.924615] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.924620] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.924658] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.924694] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.924697] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.924700] usb usb4: Product: UHCI Host Controller
[    0.924702] usb usb4: Manufacturer: Linux 3.5.0-21-generic uhci_hcd
[    0.924705] usb usb4: SerialNumber: 0000:00:1a.1
[    0.924819] hub 4-0:1.0: USB hub found
[    0.924824] hub 4-0:1.0: 2 ports detected
[    0.924906] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.924911] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.924916] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.924945] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.924979] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.924982] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.924984] usb usb5: Product: UHCI Host Controller
[    0.924987] usb usb5: Manufacturer: Linux 3.5.0-21-generic uhci_hcd
[    0.924990] usb usb5: SerialNumber: 0000:00:1d.0
[    0.925104] hub 5-0:1.0: USB hub found
[    0.925108] hub 5-0:1.0: 2 ports detected
[    0.925191] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.925195] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.925200] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.925229] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.925264] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.925267] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.925270] usb usb6: Product: UHCI Host Controller
[    0.925272] usb usb6: Manufacturer: Linux 3.5.0-21-generic uhci_hcd
[    0.925275] usb usb6: SerialNumber: 0000:00:1d.1
[    0.925397] hub 6-0:1.0: USB hub found
[    0.925401] hub 6-0:1.0: 2 ports detected
[    0.925483] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.925487] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.925492] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.925521] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.925559] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.925562] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.925565] usb usb7: Product: UHCI Host Controller
[    0.925567] usb usb7: Manufacturer: Linux 3.5.0-21-generic uhci_hcd
[    0.925570] usb usb7: SerialNumber: 0000:00:1d.2
[    0.925682] hub 7-0:1.0: USB hub found
[    0.925686] hub 7-0:1.0: 2 ports detected
[    0.925824] usbcore: registered new interface driver libusual
[    0.925885] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.928974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.928980] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.929095] mousedev: PS/2 mouse device common for all mice
[    0.929242] rtc_cmos 00:03: RTC can wake from S4
[    0.929395] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.929429] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.929488] device-mapper: uevent: version 1.0.3
[    0.929567] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.929603] EISA: Probing bus 0 at eisa.0
[    0.929606] EISA: Cannot allocate resource for mainboard
[    0.929609] Cannot allocate resource for EISA slot 1
[    0.929610] Cannot allocate resource for EISA slot 2
[    0.929612] Cannot allocate resource for EISA slot 3
[    0.929614] Cannot allocate resource for EISA slot 4
[    0.929616] Cannot allocate resource for EISA slot 5
[    0.929617] Cannot allocate resource for EISA slot 6
[    0.929619] Cannot allocate resource for EISA slot 7
[    0.929621] Cannot allocate resource for EISA slot 8
[    0.929623] EISA: Detected 0 cards.
[    0.929676] cpuidle: using governor ladder
[    0.929742] cpuidle: using governor menu
[    0.929744] EFI Variables Facility v0.08 2004-May-17
[    0.929924] ashmem: initialized
[    0.930069] TCP: cubic registered
[    0.930189] NET: Registered protocol family 10
[    0.930397] NET: Registered protocol family 17
[    0.930408] Key type dns_resolver registered
[    0.930492] Using IPI No-Shortcut mode
[    0.930582] PM: Hibernation image not present or could not be loaded.
[    0.930596] registered taskstats version 1
[    0.932756] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.933448] Key type trusted registered
[    0.935559] Key type encrypted registered
[    0.938546]   Magic number: 8:815:907
[    0.938656] rtc_cmos 00:03: setting system clock to 2012-12-28 22:52:20 UTC (1356735140)
[    0.939586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.939589] EDD information not available.
[    1.061818] isapnp: No Plug & Play device found
[    1.066472] scsi 0:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCCT10N A104 PQ: 0 ANSI: 5
[    1.071753] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.071758] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.071967] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.072110] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.692153] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.692174] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.700569] ata3.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7KP, max UDMA/100
[    1.700575] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.716545] ata3.00: configured for UDMA/100
[    1.716756] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    1.716917] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.716925] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.716981] sd 2:0:0:0: [sda] Write Protect is off
[    1.716985] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.717051] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.774563]  sda: sda1 sda2 < sda5 >
[    1.775138] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.244245] ata4.01: failed to resume link (SControl 0)
[    2.244300] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.244326] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.244511] Freeing unused kernel memory: 756k freed
[    2.244878] Write protecting the kernel text: 5964k
[    2.244913] Write protecting the kernel read-only data: 2428k
[    2.244914] NX-protecting the kernel data: 4276k
[    2.265473] udevd[101]: starting version 175
[    2.323622] wmi: Mapper loaded
[    2.356666] [drm] Initialized drm 1.1.0 20060810
[    2.364658] i915 0000:00:02.0: setting latency timer to 64
[    2.364969] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    2.364979] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.364981] [drm] Driver supports precise vblank timestamp query.
[    2.365025] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.368858] tg3.c:v3.123 (March 21, 2012)
[    2.393987] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1d:09:a3:aa:b9
[    2.393993] tg3 0000:09:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.393997] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.394000] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.448169] firewire_ohci 0000:03:01.4: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10
[    2.516055] composite sync not supported
[    2.860342] [drm] initialized overlay support
[    2.864478] composite sync not supported
[    2.948223] firewire_core 0000:03:01.4: created device fw0: GUID 484fc0000dac21a1, S400
[    3.179037] fbcon: inteldrmfb (fb0) is primary device
[    3.179091] Console: switching to colour frame buffer device 128x48
[    3.179121] fb0: inteldrmfb frame buffer device
[    3.179123] drm: registered panic notifier
[    3.191298] acpi device:36: registered as cooling_device2
[    3.191524] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    3.191582] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[    3.191875] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    3.191897] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.479984] composite sync not supported
[    8.778872] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    8.778877] EXT4-fs (sda1): write access will be enabled during recovery
[   11.281030] EXT4-fs (sda1): recovery complete
[   11.288447] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   41.891573] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.940945] udevd[415]: starting version 175
[   42.004234] lp: driver loaded but no devices found
[   42.139077] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   42.171560] cfg80211: Calling CRDA to update world regulatory domain
[   42.277824] type=1400 audit(1356735181.834:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=655 comm="apparmor_parser"
[   42.278317] type=1400 audit(1356735181.834:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=655 comm="apparmor_parser"
[   42.279026] type=1400 audit(1356735181.834:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=655 comm="apparmor_parser"
[   42.293316] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \_SB_.PCI0.VID_.TCOI 1 (20120320/utaddress-251)
[   42.293326] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   42.293329] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   42.310275] Bluetooth: Core ver 2.16
[   42.310301] NET: Registered protocol family 31
[   42.310303] Bluetooth: HCI device and connection manager initialized
[   42.310306] Bluetooth: HCI socket layer initialized
[   42.310307] Bluetooth: L2CAP socket layer initialized
[   42.310313] Bluetooth: SCO socket layer initialized
[   42.318768] ppdev: user-space parallel port driver
[   42.324552] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0200]
[   42.324582] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   42.330918] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.330922] Bluetooth: BNEP filters: protocol multicast
[   42.342588] type=1400 audit(1356735181.898:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=703 comm="apparmor_parser"
[   42.343304] type=1400 audit(1356735181.898:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=703 comm="apparmor_parser"
[   42.360905] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   42.360909] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   42.416238] Bluetooth: RFCOMM TTY layer initialized
[   42.416245] Bluetooth: RFCOMM socket layer initialized
[   42.416247] Bluetooth: RFCOMM ver 1.11
[   42.419848] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   42.419854] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   42.420167] iwl3945 0000:0c:00.0: irq 44 for MSI/MSI-X
[   42.421117] Registered led device: phy0-led
[   42.421148] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   42.440102] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   42.453267] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   42.453274] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   42.453278] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   42.456604] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   42.456609] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   42.465029]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   42.481457] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xf6a00000-0xf6afffff]
[   42.481463] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6a00000-0xf6afffff:
[   42.481479]  excluding 0xf6af0000-0xf6afffff
[   42.481484] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   42.481487] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff:
[   42.481501]  excluding 0x80000000-0x83ffffff
[   42.547127] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[   42.571442] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   42.584933] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   42.657565] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   42.657724] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   42.667987] init: failsafe main process (790) killed by TERM signal
[   42.770223] type=1400 audit(1356735182.326:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=897 comm="apparmor_parser"
[   42.770632] type=1400 audit(1356735182.326:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=897 comm="apparmor_parser"
[   42.775324] type=1400 audit(1356735182.330:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=898 comm="apparmor_parser"
[   42.776931] type=1400 audit(1356735182.334:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=898 comm="apparmor_parser"
[   42.783996] type=1400 audit(1356735182.338:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=900 comm="apparmor_parser"
[   42.861734] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   42.875224] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   42.885993] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   42.885998] cfg80211: World regulatory domain updated:
[   42.886000] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.886003] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.886006] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.886008] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.886011] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.886013] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.987652] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[   42.989585] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   43.002315] kvm: disabled by bios
[   43.021161] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   43.022664]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   43.051166] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   43.053671] kvm: disabled by bios
[   43.062359]  excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   43.062793] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   43.071342]  clean.
[   43.071388] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   43.074831]  excluding 0xc80-0xcbf
[   43.075015] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   43.075023]  excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   43.075057] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   43.077529]  clean.
[   43.077570] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   43.077590]  excluding 0x60000000-0x60ffffff
[   43.077613] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   43.082769]  clean.
[   43.125520] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   43.145671] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   43.190534] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   43.197123] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.197412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.200539] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   43.236226] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.236650] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.289863] vboxdrv: Found 2 processor cores.
[   43.290389] vboxdrv: fAsync=0 offMin=0x21c offMax=0xf0a
[   43.290472] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   43.290474] vboxdrv: Successfully loaded version 4.2.6 (interface 0x001a0004).
[   43.502467] vboxpci: IOMMU not found (not registered)
[   43.577662] composite sync not supported
[   43.752997] composite sync not supported
[   46.312081] Adding 2085884k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2085884k 
[   47.107269] composite sync not supported
[   49.583245] composite sync not supported
[  112.855299] composite sync not supported
[  113.451483] composite sync not supported
[  114.449900] composite sync not supported
[  114.904334] composite sync not supported
[  135.471729] composite sync not supported
[  177.244064] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[  177.386705] usb 2-1: New USB device found, idVendor=0bda, idProduct=8187
[  177.386711] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  177.386714] usb 2-1: Product: RTL8187_Wireless
[  177.386717] usb 2-1: Manufacturer: Manufacturer_Realtek_RTL8187_
[  177.386719] usb 2-1: SerialNumber: XXXXXXXXXXXX
[  177.673995] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  177.674000] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674003] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  177.674005] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674007] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  177.674010] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674012] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  177.674014] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674016] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  177.674018] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674020] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  177.674023] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674025] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  177.674027] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674029] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  177.674031] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674033] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  177.674036] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674038] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  177.674040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674042] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  177.674044] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.674046] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  177.674049] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.674051] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  177.674053] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.674055] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  177.674058] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.674202] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  177.674448] ieee80211 phy1: hwaddr XX:XX:XX:XX:XX:XX, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  177.688707] rtl8187: Customer ID is 0xFF
[  177.688786] Registered led device: rtl8187-phy1::radio
[  177.688832] Registered led device: rtl8187-phy1::tx
[  177.688856] Registered led device: rtl8187-phy1::rx
[  177.689682] rtl8187: wireless switch is on
[  177.689721] usbcore: registered new interface driver rtl8187
[  180.213543] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  180.213887] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  228.368793] wlan1: authenticate with XX:XX:XX:XX:XX:XX
[  228.478673] wlan1: send auth to XX:XX:XX:XX:XX:XX (try 1/3)
[  228.480834] wlan1: authenticated
[  228.540041] wlan1: associate with XX:XX:XX:XX:XX:XX (try 1/3)
[  228.542944] wlan1: RX AssocResp from XX:XX:XX:XX:XX:XX (capab=0x401 status=0 aid=5)
[  228.543698] wlan1: associated
[  228.543894] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

```

Thank's again for any help!

---

### Post by jstthe01 on 2013-03-28
Maybe I'm missing someting? Is there a reason that no one has ever replied to this qestion in this thread?
Just wondering??

---

### Post by chili555 on 2013-04-01
Why is the internal Intel wireless device not working as expected. I suspect the two devices with two drivers may be conflicting. I also suspect the Intel would perform better than any USB.

---

### Post by jstthe01 on 2013-04-15
> **chili555 said:**
> Why is the internal Intel wireless device not working as expected. I suspect the two devices with two drivers may be conflicting. I also suspect the Intel would perform better than any USB.

Well the internal Intel is working fine but I need the alpha to work correctly for the range, I'm on the  alpha now and it's working fine, just sometimes it won't. Idk what it is, also I have to enter the modbrobe rtl8187 command every time I reboot or it does not even see the alfa adapter. I have the same problem on another laptop that I got Kali- Linux installed on. I don't have to enter the modprobe command in kali but have the same problem that the adapter sometimes wants to work fine and sometimes it won't even load a web page, hope you guys can give me a hand, thank's in advance!!

---

### Post by chili555 on 2013-04-16
If you want to use the Alpha full-time, I suggest you blacklist the internal and add the driver for the Alpha to *modules*. If that is what you want to do, then open a terminal and do:```
sudo su
echo "blacklist iwl3945" >> /etc/modprobe.d/blacklist.conf
echo rtl8187 >> /etc/modules
modprobe -r iwl3945
modprobe rtl8187
exit
```You should be all set.

---

