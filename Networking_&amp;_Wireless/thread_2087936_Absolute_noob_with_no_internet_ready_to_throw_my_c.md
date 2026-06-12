---
title: "Absolute noob with no internet ready to throw my computer out the window"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by Wobbs91 on 2012-11-25
I have installed Ubuntu 12.04  LTS on my PC. I have no internet. I have my USB wifi hooked up and windows drivers and ndiswrapper but I cannot install anything because the install button is gray. I have looked for hours and no luck. I feel like going back to Windows 7 but and willing to have this as my absolute last resort. Thanks for any and all help.

---

### Post by squenson on 2012-11-25
Not all USB wi-fi dongles are compatible with Ubuntu, their drivers simply are not adapted to this OS. Which model do you have?

---

### Post by Bucky Ball on 2012-11-25
Welcome to the forums. Don't do any throwing away just yet. 

ndiswrapper is largely superseded and you may have gotten that info from an old site. Avoid. If you installed that before doing an update with an ethernet cable then ndiswrapper could be preventing your card working! Let me assure you that it will almost definitely prevent you getting anything else to work and I would totally uninstall it before attempting anything else. Have you looked in Additional Drivers? 

Post the results of these three commands (run one at a time) from a terminal (Applications>Accessories>Terminal) with the dongle plugged in:
```

sudo lshw -C network
iwconfig
lsusb
```You also don't provide any details on the USB dongle ... What is it???

PS: Save some sweat and if you can't find what your looking for elsewhere online or are confused or unsure about what you do find, make the forums your next resort! The forums and its users are here to help ... ;)

---

### Post by lisati on 2012-11-25
*Thread moved to **Networking & Wireless**.*

---

### Post by Wobbs91 on 2012-11-25
> **squenson said:**
> Not all USB wi-fi dongles are compatible with Ubuntu, their drivers simply are not adapted to this OS. Which model do you have?

I have a d-link DWA 130c. I have seen code that you have to type and it works or something but IDK where to start with code and stuff. I have windows drivers from xp and vista.

---

### Post by Bucky Ball on 2012-11-25
Have you plugged in an ethernet cable and done updates with that device plugged in?

As I mentioned, not much will probably work, code or otherwise, with ndiswrapper installed. Other thing is this appears to have N capabilities and your access point/router may not. That could actually be the problem.

Please read post #3 again and post the requested info. Thanks. That will give an idea of where you're currently at.

---

### Post by Wobbs91 on 2012-11-25
> **Bucky Ball said:**
> Have you plugged in an ethernet cable and done updates with that device plugged in?

As I mentioned, not much will probably work, code or otherwise, with ndiswrapper installed. Other thing is this appears to have N capabilities and your access point/router may not. That could actually be the problem.

Please read post #3 again and post the requested info. Thanks. That will give an idea of where you're currently at.

I do not have access to an Ethernet cable and was unsuccessful in installing ndiswrapper. The wifi adapter has worked with my current router in Windows 7.

---

### Post by Bucky Ball on 2012-11-25
Post the results of these commands and forget about ndiswrapper then. Cheers.

sudo lshw -C network
iwconfig
lsusb

If you can't get online with the machine you are going to need to drop them to a usb dongle. You probably couldn't install ndiswrapper because you are not online. That will prevent you installing anything except from local media.

As for the ethernet cable, it would make things much easier if you could beg, borrow, or steal one or get the machine to somewhere you can get online ...

---

### Post by Wobbs91 on 2012-11-25
> **Bucky Ball said:**
> Post the results of these commands and forget about ndiswrapper then. Cheers.

sudo lshw -C network
iwconfig
lsusb

If you can't get online with the machine you are going to need to drop them to a usb dongle. You probably couldn't install ndiswrapper because you are not online. That will prevent you installing anything except from local media.

As for the ethernet cable, it would make things much easier if you could beg, borrow, or steal one or get the machine to somewhere you can get online ...


```

~$ sudo lshw -C network
PCI (sysfs)  

  *-network DISABLED      
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:6e:fd:24
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:f9eff000-f9efffff ioport:ccc0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:22:b0:73:fb:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/g





iwconfig
lo        no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.





 isusb
No command 'isusb' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
isusb: command not found


```

If I could get to an Ethernet cable, what would I need to do?

---

### Post by Bucky Ball on 2012-11-26
Okay, you're actually looking good. You have a driver already installed automagically, probably for your dongle unless you have an internal card:

driver=rtl819xU

 You are not associated to any access point though. You need to find out the name of your network. When you left click the network icon, do you get a list of available networks? Is yours there?

You need to know the correct name and the security type and details. You can then right click the network icon and 'Edit connections' and set up your connection in Network Manager ...

The last command was 'lsusb' not 'isusb'.

PS: You don't have a wireless toggle switch and it is off? Is there a wireless light? And if you had an ethernet cable you could install things you might need and do an update which might this quickly.

---

### Post by Wobbs91 on 2012-11-26
When I click on the network icon, it says "device not ready" under wireless networks. 

My USB wifi adapter has a light but it is not on. There are no switches on it.

---

### Post by chili555 on 2012-11-27
Buckie Ball and I have been discussing this in the back room and we're puzzled that both ethernet and wireless say:> *-network [COLOR="Red"]DISABLED[/COLOR]      
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:6e:fd:24
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:f9eff000-f9efffff ioport:ccc0(size=64)
  *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:22:b0:73:fb:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/gAside from that, everything looks very good. We are both wondering if there is either a setting in the BIOS that enables/disables these devices or an ACPI problem with the PCI slots.

Please check in the BIOS for any such settings. In many cases, resetting the BIOS to defaults resolves a lot of problems. 

Let's look for ACPI issues:```
dmesg | grep -i -e warn -e error
```

---

### Post by Wobbs91 on 2012-11-27
> **chili555 said:**
> Buckie Ball and I have been discussing this in the back room and we're puzzled that both ethernet and wireless say:Aside from that, everything looks very good. We are both wondering if there is either a setting in the BIOS that enables/disables these devices or an ACPI problem with the PCI slots.

Please check in the BIOS for any such settings. In many cases, resetting the BIOS to defaults resolves a lot of problems. 

Let's look for ACPI issues:```
dmesg | grep -i -e warn -e error
```

```

[    1.340046] system 00:07: [io  0xa200-0xa2fe] has been reserved

[    1.340051] system 00:07: [io  0xa300-0xa3fe] has been reserved

[    1.340055] system 00:07: [io  0xa400-0xa4fe] has been reserved

[    1.340060] system 00:07: [io  0xa500-0xa5fe] has been reserved

[    1.340064] system 00:07: [io  0xa600-0xa6fe] has been reserved

[    1.340069] system 00:07: [io  0xa700-0xa7fe] has been reserved

[    1.340073] system 00:07: [io  0xa800-0xa8fe] has been reserved

[    1.340078] system 00:07: [io  0xa900-0xa9fe] has been reserved

[    1.340083] system 00:07: [io  0xaa00-0xaafe] has been reserved

[    1.340087] system 00:07: [io  0xab00-0xabfe] has been reserved

[    1.340092] system 00:07: [io  0xac00-0xacfe] has been reserved

[    1.340097] system 00:07: [io  0xad00-0xadfe] has been reserved

[    1.340101] system 00:07: [io  0xae00-0xaefe] has been reserved

[    1.340106] system 00:07: [io  0xaf00-0xaffe] has been reserved

[    1.340111] system 00:07: [mem 0xf0000000-0xf3ffffff] has been reserved

[    1.340115] system 00:07: [mem 0xfeda0000-0xfedacfff] has been reserved

[    1.340120] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)

[    1.340129] pnp: PnP ACPI: found 8 devices

[    1.340132] ACPI: ACPI bus type pnp unregistered

[    1.340137] PnPBIOS: Disabled by ACPI PNP

[    1.377667] PCI: max bus depth: 1 pci_try_num: 2

[    1.377719] pci 0000:00:1c.5: BAR 14: assigned [mem 0xe0000000-0xe01fffff]

[    1.377725] pci 0000:00:1c.5: BAR 15: assigned [mem 0xe0200000-0xe03fffff 64bit pref]

[    1.377731] pci 0000:00:1c.5: BAR 13: assigned [io  0x1000-0x1fff]

[    1.377735] pci 0000:00:1c.4: BAR 14: assigned [mem 0xe0400000-0xe05fffff]

[    1.377740] pci 0000:00:1c.4: BAR 15: assigned [mem 0xe0600000-0xe07fffff 64bit pref]

[    1.377746] pci 0000:00:1c.4: BAR 13: assigned [io  0x3000-0x3fff]

[    1.377751] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe0800000-0xe09fffff 64bit pref]

[    1.377757] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]

[    1.377762] pci 0000:00:01.0: PCI bridge to [bus 01-01]

[    1.377766] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]

[    1.377771] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]

[    1.377776] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]

[    1.377783] pci 0000:00:1c.0: PCI bridge to [bus 02-02]

[    1.377787] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]

[    1.377794] pci 0000:00:1c.0:   bridge window [mem 0xf9f00000-0xf9ffffff]

[    1.377799] pci 0000:00:1c.0:   bridge window [mem 0xe0800000-0xe09fffff 64bit pref]

[    1.377807] pci 0000:00:1c.4: PCI bridge to [bus 03-03]

[    1.377811] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]

[    1.377817] pci 0000:00:1c.4:   bridge window [mem 0xe0400000-0xe05fffff]

[    1.377823] pci 0000:00:1c.4:   bridge window [mem 0xe0600000-0xe07fffff 64bit pref]

[    1.377830] pci 0000:00:1c.5: PCI bridge to [bus 04-04]

[    1.377835] pci 0000:00:1c.5:   bridge window [io  0x1000-0x1fff]

[    1.377841] pci 0000:00:1c.5:   bridge window [mem 0xe0000000-0xe01fffff]

[    1.377847] pci 0000:00:1c.5:   bridge window [mem 0xe0200000-0xe03fffff 64bit pref]

[    1.377855] pci 0000:00:1e.0: PCI bridge to [bus 05-05]

[    1.377859] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]

[    1.377865] pci 0000:00:1e.0:   bridge window [mem 0xf9e00000-0xf9efffff]

[    1.377891] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    1.377897] pci 0000:00:01.0: setting latency timer to 64

[    1.377906] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    1.377911] pci 0000:00:1c.0: setting latency timer to 64

[    1.377919] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    1.377925] pci 0000:00:1c.4: setting latency timer to 64

[    1.377938] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17

[    1.377944] pci 0000:00:1c.5: setting latency timer to 64

[    1.377952] pci 0000:00:1e.0: setting latency timer to 64

[    1.377957] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]

[    1.377961] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]

[    1.377964] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]

[    1.377968] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]

[    1.377971] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]

[    1.377974] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]

[    1.377977] pci_bus 0000:02: resource 1 [mem 0xf9f00000-0xf9ffffff]

[    1.377981] pci_bus 0000:02: resource 2 [mem 0xe0800000-0xe09fffff 64bit pref]

[    1.377984] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]

[    1.377987] pci_bus 0000:03: resource 1 [mem 0xe0400000-0xe05fffff]

[    1.377990] pci_bus 0000:03: resource 2 [mem 0xe0600000-0xe07fffff 64bit pref]

[    1.377994] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]

[    1.377997] pci_bus 0000:04: resource 1 [mem 0xe0000000-0xe01fffff]

[    1.378000] pci_bus 0000:04: resource 2 [mem 0xe0200000-0xe03fffff 64bit pref]

[    1.378004] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]

[    1.378007] pci_bus 0000:05: resource 1 [mem 0xf9e00000-0xf9efffff]

[    1.378010] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]

[    1.378013] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]

[    1.378062] NET: Registered protocol family 2

[    1.378158] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    1.378499] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    1.379041] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    1.379312] TCP: Hash tables configured (established 131072 bind 65536)

[    1.379315] TCP reno registered

[    1.379319] UDP hash table entries: 512 (order: 2, 16384 bytes)

[    1.379329] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)

[    1.379418] NET: Registered protocol family 1

[    1.379470] pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[    1.379491] pci 0000:00:1d.0: PCI INT A disabled

[    1.379507] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22

[    1.379527] pci 0000:00:1d.1: PCI INT B disabled

[    1.379542] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    1.379561] pci 0000:00:1d.2: PCI INT C disabled

[    1.379576] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23

[    1.379595] pci 0000:00:1d.3: PCI INT D disabled

[    1.379605] pci 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[    1.379639] pci 0000:00:1d.7: PCI INT A disabled

[    1.379676] pci 0000:01:00.0: Boot video device

[    1.379694] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling

[    1.379702] PCI: CLS 64 bytes, default 64

[    1.379709] Simple Boot Flag at 0x7a set to 0x1

[    1.380193] audit: initializing netlink socket (disabled)

[    1.380205] type=2000 audit(1354042566.376:1): initialized

[    1.411716] highmem bounce pool size: 64 pages

[    1.411727] HugeTLB registered 2 MB page size, pre-allocated 0 pages

[    1.425381] VFS: Disk quotas dquot_6.5.2

[    1.425472] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    1.426317] fuse init (API version 7.17)

[    1.426468] msgmni has been set to 1688

[    1.426957] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)

[    1.426999] io scheduler noop registered

[    1.427002] io scheduler deadline registered

[    1.427012] io scheduler cfq registered (default)

[    1.427169] pcieport 0000:00:01.0: setting latency timer to 64

[    1.427215] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X

[    1.427285] pcieport 0000:00:1c.0: setting latency timer to 64

[    1.427332] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X

[    1.427411] pcieport 0000:00:1c.4: setting latency timer to 64

[    1.427458] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X

[    1.427536] pcieport 0000:00:1c.5: setting latency timer to 64

[    1.427583] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X

[    1.427700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    1.427740] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    1.427964] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0

[    1.427973] ACPI: Power Button [VBTN]

[    1.428069] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

[    1.428075] ACPI: Power Button [PWRF]

[    1.491269] ERST: Table is not found!

[    1.491272] GHES: HEST is not enabled!

[    1.491324] isapnp: Scanning for PnP cards...

[    1.491380] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled

[    1.844467] isapnp: No Plug & Play device found

[    1.924287] Linux agpgart interface v0.103

[    1.926614] brd: module loaded

[    1.927680] loop: module loaded

[    1.927862] ahci 0000:00:1f.2: version 3.0

[    1.927886] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20

[    1.927942] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X

[    1.928050] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode

[    1.928056] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 

[    1.928062] ahci 0000:00:1f.2: setting latency timer to 64

[    1.928946] scsi0 : ahci

[    1.929076] scsi1 : ahci

[    1.929188] scsi2 : ahci

[    1.929298] scsi3 : ahci

[    1.929377] ata1: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd00 irq 44

[    1.929381] ata2: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbd80 irq 44

[    1.929385] ata3: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe00 irq 44

[    1.929389] ata4: SATA max UDMA/133 abar m1024@0xfebfbc00 port 0xfebfbe80 irq 44

[    1.929460] ata_piix 0000:00:1f.1: version 2.13

[    1.929473] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    1.929526] ata_piix 0000:00:1f.1: setting latency timer to 64

[    1.929998] scsi4 : ata_piix

[    1.930120] scsi5 : ata_piix

[    1.930190] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14

[    1.930194] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15

[    1.930798] Fixed MDIO Bus: probed

[    1.930835] tun: Universal TUN/TAP device driver, 1.6

[    1.930838] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

[    1.930933] PPP generic driver version 2.4.2

[    1.931100] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    1.931130] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[    1.931143] ata6: port disabled--ignoring

[    1.931150] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[    1.931156] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    1.931217] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1

[    1.931241] ehci_hcd 0000:00:1d.7: using broken periodic workaround

[    1.931253] ehci_hcd 0000:00:1d.7: debug port 1

[    1.935125] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported

[    1.935143] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800

[    1.948019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00

[    1.948207] hub 1-0:1.0: USB hub found

[    1.948214] hub 1-0:1.0: 8 ports detected

[    1.948339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    1.948361] uhci_hcd: USB Universal Host Controller Interface driver

[    1.948388] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[    1.948399] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[    1.948403] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    1.948468] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2

[    1.948494] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80

[    1.948673] hub 2-0:1.0: USB hub found

[    1.948679] hub 2-0:1.0: 2 ports detected

[    1.948774] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22

[    1.948784] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[    1.948789] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    1.948845] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3

[    1.948881] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60

[    1.949060] hub 3-0:1.0: USB hub found

[    1.949071] hub 3-0:1.0: 2 ports detected

[    1.949171] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    1.949181] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[    1.949185] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    1.949242] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4

[    1.949278] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40

[    1.949461] hub 4-0:1.0: USB hub found

[    1.949467] hub 4-0:1.0: 2 ports detected

[    1.949560] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23

[    1.949571] uhci_hcd 0000:00:1d.3: setting latency timer to 64

[    1.949575] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[    1.949629] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5

[    1.949665] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20

[    1.949841] hub 5-0:1.0: USB hub found

[    1.949847] hub 5-0:1.0: 2 ports detected

[    1.950009] usbcore: registered new interface driver libusual

[    1.950069] i8042: PNP: No PS/2 controller found. Probing ports directly.

[    1.952902] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.952912] serio: i8042 AUX port at 0x60,0x64 irq 12

[    1.953127] mousedev: PS/2 mouse device common for all mice

[    1.953365] rtc_cmos 00:05: RTC can wake from S4

[    1.953506] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0

[    1.953535] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs

[    1.953623] device-mapper: uevent: version 1.0.3

[    1.953743] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com

[    1.953796] EISA: Probing bus 0 at eisa.0

[    1.953801] EISA: Cannot allocate resource for mainboard

[    1.953804] Cannot allocate resource for EISA slot 1

[    1.953808] Cannot allocate resource for EISA slot 2

[    1.953811] Cannot allocate resource for EISA slot 3

[    1.953814] Cannot allocate resource for EISA slot 4

[    1.953817] Cannot allocate resource for EISA slot 5

[    1.953820] Cannot allocate resource for EISA slot 6

[    1.953832] EISA: Detected 0 cards.

[    1.953844] cpufreq-nforce2: No nForce2 chipset.

[    1.953849] cpuidle: using governor ladder

[    1.953852] cpuidle: using governor menu

[    1.953854] EFI Variables Facility v0.08 2004-May-17

[    1.954241] TCP cubic registered

[    1.954423] NET: Registered protocol family 10

[    1.955294] NET: Registered protocol family 17

[    1.955301] Registering the dns_resolver key type

[    1.955329] Using IPI No-Shortcut mode

[    1.955508] PM: Hibernation image not present or could not be loaded.

[    1.955531] registered taskstats version 1

[    1.970119]   Magic number: 4:860:949

[    1.970164] tty tty6: hash matches

[    1.970218] rtc_cmos 00:05: setting system clock to 2012-11-27 18:56:07 UTC (1354042567)

[    1.970244] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.970248] EDD information not available.

[    2.108309] ata5.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PS08, max UDMA/66

[    2.108316] ata5.00: limited to UDMA/33 due to 40-wire cable

[    2.140206] ata5.00: configured for UDMA/33

[    2.248028] ata2: SATA link down (SStatus 0 SControl 300)

[    2.248056] ata4: SATA link down (SStatus 0 SControl 300)

[    2.248084] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

[    2.248102] ata3: SATA link down (SStatus 0 SControl 300)

[    2.248954] ata1.00: ATA-8: WDC WD6400AAKS-22A7B2, 01.03B01, max UDMA/133

[    2.248959] ata1.00: 1250263728 sectors, multi 8: LBA48 NCQ (depth 31/32), AA

[    2.249904] ata1.00: configured for UDMA/133

[    2.250049] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-2 01.0 PQ: 0 ANSI: 5

[    2.250297] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)

[    2.250379] sd 0:0:0:0: [sda] Write Protect is off

[    2.250383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    2.250418] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    2.250514] sd 0:0:0:0: Attached scsi generic sg0 type 0

[    2.251714] scsi 4:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PS08 PQ: 0 ANSI: 5

[    2.254094] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray

[    2.254098] cdrom: Uniform CD-ROM driver Revision: 3.20

[    2.254259] sr 4:0:0:0: Attached scsi CD-ROM sr0

[    2.254408] sr 4:0:0:0: Attached scsi generic sg1 type 5

[    2.260025] usb 1-2: new high-speed USB device number 2 using ehci_hcd

[    2.274184]  sda: sda1 sda2 < sda5 >

[    2.274627] sd 0:0:0:0: [sda] Attached SCSI disk

[    2.274731] Freeing unused kernel memory: 740k freed

[    2.275174] Write protecting the kernel text: 5816k

[    2.275202] Write protecting the kernel read-only data: 2376k

[    2.275205] NX-protecting the kernel data: 4424k

[    2.299209] udevd[96]: starting version 175

[    2.376064] Refined TSC clocksource calibration: 3191.999 MHz.

[    2.376073] Switching to clocksource tsc

[    2.385823] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI

[    2.385827] e100: Copyright(c) 1999-2006 Intel Corporation

[    2.385879] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20

[    2.413903] e100 0000:05:08.0: PME# disabled

[    2.414679] e100 0000:05:08.0: eth0: addr 0xf9eff000, irq 20, MAC addr 00:12:3f:6e:fd:24

[    2.632032] usb 1-8: new high-speed USB device number 5 using ehci_hcd

[    2.666990] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

[    2.767593] Initializing USB Mass Storage driver...

[    2.767730] scsi6 : usb-storage 1-8:1.0

[    2.767842] usbcore: registered new interface driver usb-storage

[    2.767845] USB Mass Storage support registered.

[    3.004021] usb 4-1: new low-speed USB device number 2 using uhci_hcd

[    3.436025] usb 4-2: new low-speed USB device number 3 using uhci_hcd

[    3.764609] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS

[    3.765526] sd 6:0:0:0: Attached scsi generic sg2 type 0

[    3.766117] sd 6:0:0:0: [sdb] 15682559 512-byte logical blocks: (8.02 GB/7.47 GiB)

[    3.766584] sd 6:0:0:0: [sdb] Write Protect is off

[    3.766589] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08

[    3.767081] sd 6:0:0:0: [sdb] No Caching mode page present

[    3.767085] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    3.769330] sd 6:0:0:0: [sdb] No Caching mode page present

[    3.769334] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    3.770787]  sdb: sdb1

[    3.772955] sd 6:0:0:0: [sdb] No Caching mode page present

[    3.772958] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    3.772962] sd 6:0:0:0: [sdb] Attached SCSI removable disk

[    8.995528] ADDRCONF(NETDEV_UP): eth0: link is not ready

[    9.039674] udevd[317]: starting version 175

[    9.086510] lp: driver loaded but no devices found

[    9.088693] Adding 3142652k swap on /dev/sda5.  Priority:-1 extents:1 across:3142652k 

[    9.117431] wmi: Mapper loaded

[    9.130987] [drm] Initialized drm 1.1.0 20060810

[    9.198694] intel_rng: Firmware space is locked read-only. If you can't or

[    9.198697] intel_rng: don't want to disable this in firmware setup, and if

[    9.198699] intel_rng: you are certain that your system has a functional

[    9.198700] intel_rng: RNG, try using the 'no_fwh_detect' option.

[    9.201577] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    9.201588] nouveau 0000:01:00.0: setting latency timer to 64

[    9.209426] leds_ss4200: no LED devices found

[    9.226191] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

[    9.233610] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2

[    9.234148] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x096000c1)

[    9.234575] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-1/input0

[    9.247726] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN

[    9.265937] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3

[    9.267283] generic-usb 0003:413C:3012.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.2-2/input0

[    9.267347] usbcore: registered new interface driver usbhid

[    9.267351] usbhid: USB HID core driver

[    9.313040] [drm] nouveau 0000:01:00.0: ... appears to be valid

[    9.313046] [drm] nouveau 0000:01:00.0: BIT BIOS found

[    9.313051] [drm] nouveau 0000:01:00.0: Bios version 62.94.2a.00

[    9.313055] [drm] nouveau 0000:01:00.0: TMDS table version 2.0

[    9.313059] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0

[    9.313065] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028

[    9.313069] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030

[    9.313072] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028

[    9.313076] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00020030

[    9.313079] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080

[    9.313083] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4

[    9.313087] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07

[    9.313091] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08

[    9.313094] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff

[    9.313098] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff

[    9.313101] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff

[    9.313106] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD0BE

[    9.337954] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.

[    9.338238] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD4D3

[    9.341247] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE4C4

[    9.341256] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE60D

[    9.342330] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE849

[    9.342334] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE8AE

[    9.362184] [drm] nouveau 0000:01:00.0: 0xE8AE: Condition still not met after 20ms, skipping following opcodes

[    9.385317] [drm] nouveau 0000:01:00.0: 1 available performance level(s)

[    9.385325] [drm] nouveau 0000:01:00.0: 3: core 550MHz shader 1375MHz memory 500MHz fanspeed 100%

[    9.385344] [drm] nouveau 0000:01:00.0: c: core 400MHz shader 800MHz memory 499MHz

[    9.400495] ieee80211_crypt: registered algorithm 'NULL'

[    9.400500] ieee80211_crypt: registered algorithm 'TKIP'

[    9.400503] ieee80211_crypt: registered algorithm 'CCMP'

[    9.400506] ieee80211_crypt: registered algorithm 'WEP'

[    9.400508] 

[    9.400509] Linux kernel driver for RTL8192 based WLAN cards

[    9.400512] Copyright (c) 2007-2008, Realsil Wlan

[    9.402472] [TTM] Zone  kernel: Available graphics memory: 432684 kiB.

[    9.402477] [TTM] Zone highmem: Available graphics memory: 1548104 kiB.

[    9.402480] [TTM] Initializing pool allocator.

[    9.402498] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM

[    9.403941] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)

[    9.428089] type=1400 audit(1354042574.954:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=431 comm="apparmor_parser"

[    9.428652] type=1400 audit(1354042574.954:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=431 comm="apparmor_parser"

[    9.428941] type=1400 audit(1354042574.954:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=431 comm="apparmor_parser"

[    9.435956] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown

[    9.435962] [drm] nouveau 0000:01:00.0: TV-1 has no encoders, removing

[    9.486910] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).

[    9.486915] [drm] No driver support for vblank timestamp query.

[    9.682748] Bluetooth: Core ver 2.16

[    9.683426] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)

[    9.688392] NET: Registered protocol family 31

[    9.688398] Bluetooth: HCI device and connection manager initialized

[    9.688403] Bluetooth: HCI socket layer initialized

[    9.688406] Bluetooth: L2CAP socket layer initialized

[    9.688418] Bluetooth: SCO socket layer initialized

[    9.697773] ppdev: user-space parallel port driver

[    9.720092] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[    9.720098] Bluetooth: BNEP filters: protocol multicast

[    9.729545] type=1400 audit(1354042575.254:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=594 comm="apparmor_parser"

[    9.730173] type=1400 audit(1354042575.254:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=594 comm="apparmor_parser"

[    9.730835] Bluetooth: RFCOMM TTY layer initialized

[    9.730846] Bluetooth: RFCOMM socket layer initialized

[    9.730849] Bluetooth: RFCOMM ver 1.11

[    9.791090] init: failsafe main process (558) killed by TERM signal

[    9.920250] type=1400 audit(1354042575.446:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=677 comm="apparmor_parser"

[    9.924639] type=1400 audit(1354042575.450:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=676 comm="apparmor_parser"

[    9.926458] type=1400 audit(1354042575.450:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=677 comm="apparmor_parser"

[    9.926748] type=1400 audit(1354042575.450:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=677 comm="apparmor_parser"

[    9.952844] type=1400 audit(1354042575.478:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=685 comm="apparmor_parser"

[    9.974063] ADDRCONF(NETDEV_UP): eth0: link is not ready

[    9.974932] ADDRCONF(NETDEV_UP): eth0: link is not ready

[    9.984120] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    9.986463] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X

[    9.986498] snd_hda_intel 0000:00:1b.0: setting latency timer to 64

[   10.041904] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4

[   10.042137] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5

[   10.042377] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6

[   10.042584] input: HDA Intel Speaker CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7

[   10.042801] input: HDA Intel Speaker Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8

[   10.043006] input: HDA Intel Speaker Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9

[   10.444118] [drm] nouveau 0000:01:00.0: allocated 1440x900 fb: 0x330000, bo f1973a00

[   10.444404] fbcon: nouveaufb (fb0) is primary device

[   10.444711] Console: switching to colour frame buffer device 180x56

[   10.444747] fb0: nouveaufb frame buffer device

[   10.444750] drm: registered panic notifier

[   10.444760] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0

[   10.664575] Dot11d_Init()

[   10.664582] End of initendpoints

[   10.665850] usbcore: registered new interface driver rtl819xU

[   10.935701] rtl819xU:request firmware fail!

[   10.935704] 

[   10.935707] rtl819xU:ERR in init_firmware()

[   10.935708] 

[   10.935711] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed

[   10.935713] 

[   10.935715] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

[   10.935717] 

[   10.935859] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   11.169928] rtl819xU:request firmware fail!

[   11.169930] 

[   11.169933] rtl819xU:ERR in init_firmware()

[   11.169935] 

[   11.169938] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed

[   11.169939] 

[   11.169942] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

[   11.169943] 

[   37.856583] audit_printk_skb: 36 callbacks suppressed

[   37.856587] type=1400 audit(1354042603.382:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1696 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0








```

---

### Post by Wobbs91 on 2012-11-27
The code "grep -i -e warn -e error" did nothing. I have reset my BIOS to defaults and still no success. My computer is a Dell Dimension 9100, not sure if that matters or not but it can't hurt...

---

### Post by chili555 on 2012-11-27
> [   9.337954] [COLOR="Red"]r8192u_usb[/COLOR]: module is from the staging directory, the quality is unknown, you have been warned.

[   10.935701] [COLOR="Red"]rtl819xU:request firmware fail![/COLOR]

[   10.935704] 

[   10.935707] rtl819xU:ERR in init_firmware()

[   10.935708] 

[   10.935711] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed

[   10.935713] 

[   10.935715] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
I assume it is the USB that we're trying to get going. The module r8192u_usb needs firmware and I'm a bit surprised it isn't installed by default. From modinfo:```
$ modinfo r8192u_usb
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
license:        GPL
<snip>
```I have attached a zip file. Please download it and transfer it on a USB key or similar and drag and drop it to your desktop. Right-click and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp Desktop/RTL8192U/*   /lib/firmware/RTL8192U 
```Insert the device. Is it working now?

---

### Post by Wobbs91 on 2012-11-27
> **chili555 said:**
> I assume it is the USB that we're trying to get going. The module r8192u_usb needs firmware and I'm a bit surprised it isn't installed by default. From modinfo:```
$ modinfo r8192u_usb
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
license:        GPL
<snip>
```I have attached a zip file. Please download it and transfer it on a USB key or similar and drag and drop it to your desktop. Right-click and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp Desktop/RTL8192U/*   /lib/firmware/RTL8192U 
```Insert the device. Is it working now?

It worked! Thanks so much!

---

### Post by Wobbs91 on 2012-11-27
Okay it says its connected but I can't load any web pages. Maybe it's a Firefox issue. I usually use chrome so I don't really know how to fix this. Any suggestions?

---

### Post by Wobbs91 on 2012-11-27
> **Wobbs91 said:**
> Okay it says its connected but I can't load any web pages. Maybe it's a Firefox issue. I usually use chrome so I don't really know how to fix this. Any suggestions?

More information: It's not Firefox. My internet works in momentary lapses (I downloaded 8MB in 30 min in Ubuntu Software Center, I have cable internet).

---

### Post by Bucky Ball on 2012-11-28
Hmm, the plot thickens. When you right click the network icon and 'Edit Connections', do you have the settings correct in there? Correct security type (WPA, WEP etc), 'Connect Automatically' and 'Available to all users' is checked? If you are running a static IP do you perhaps need to put the DNS details in there, too (if you do then you would be connected to your network (LAN) but can't get to the outside world (WAN)?

If you have working wireless in Windows or on another machine you could perhaps compare the wireless details in that setup to the one in Ubuntu and see if you can notice any differences.


Good to hear there's progress. (Cheers Chili555) ;)

---

### Post by Wobbs91 on 2012-11-29
> **Bucky Ball said:**
> Hmm, the plot thickens. When you right click the network icon and 'Edit Connections', do you have the settings correct in there? Correct security type (WPA, WEP etc), 'Connect Automatically' and 'Available to all users' is checked? If you are running a static IP do you perhaps need to put the DNS details in there, too (if you do then you would be connected to your network (LAN) but can't get to the outside world (WAN)?

If you have working wireless in Windows or on another machine you could perhaps compare the wireless details in that setup to the one in Ubuntu and see if you can notice any differences.


Good to hear there's progress. (Cheers Chili555) ;)

I looked at all the settings and things seemed to match up pretty nicely so I just ran the update process and just kept reconnecting every time the connection froze up. I guess it helped because after the updates I am now running smoothly. Thanks everyone who helped!

---

