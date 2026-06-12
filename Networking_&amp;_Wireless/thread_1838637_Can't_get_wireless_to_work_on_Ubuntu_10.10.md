---
title: "Can't get wireless to work on Ubuntu 10.10"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by njwatson32 on 2011-09-04
I installed 11.04 on my new Lenovo T420 but I was having major problems (namely that it kept logging me out randomly and programs would crash inexplicably) so I went back to 10.10.

When I got to the desktop, there was no option to search for wireless networks, which is strange because I had no trouble in 11.04.

It seems I'm missing a driver or something.

Here's all the info:

I'm running Ubuntu 10.10, 2.6.35-22-generic i686 on my new Lenovo ThinkPad T420 alongside the preloaded Windows 7.

lspci (I believe the bolded line is the relevant part, but I've included it all to be sure):
```

00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
**03:00.0 Network controller: Intel Corporation 6000 Series Gen2 (rev 34)**
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 04)

```iwconfig:
```

lo     no wireless extensions.
eth0   no wireless extensions.

```lsmod says I have iwlagn

dmesg | grep iwlagn:
```

[    3.438374] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.438377] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    3.438466] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.438496] iwlagn 0000:03:00.0: setting latency timer to 64
[    3.438568] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.447861] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[    3.447864] iwlagn 0000:03:00.0: Device SKU: 0Xb
[    3.447866] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[    3.447892] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.448062] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[    3.454445] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-5.ucode' failed.
[    3.455468] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[    3.455501] iwlagn 0000:03:00.0: no suitable firmware found!
[    3.455717] iwlagn 0000:03:00.0: PCI INT A disabled

```sudo lshw -C network (I feel like the UNCLAIMED network is the problematic one):
```

*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:67:37:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=half firmware=0.13-3 ip=165.123.172.63 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:44 memory:f2600000-f261ffff memory:f262b000-f262bfff ioport:5080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: 6000 Series Gen2
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f2500000-f2501fff

```iwlist scan:
```

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

```sudo /etc/init.d/networking restart:
```

 * Reconfiguring network interfaces... 
Ignoring unknown interface eth0=eth0.

```sudo modprobe iwlagn did nothing.

I tried installing compat-wireless ([http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2)), but it didn't work.

At this point I really don't know what to do...please help!

---

### Post by pdc on 2011-09-04
this post is directly above yours

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

it is called a stickie: always present to help folks

provide all the information it asks for: it will help you

---

### Post by njwatson32 on 2011-09-04
> **pdc said:**
> this post is directly above yours

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

it is called a stickie: always present to help folks

provide all the information it asks for: it will help you

So I added all the information...does anyone know how to help me?

---

### Post by Brianret on 2011-09-04
H[SIZE=3]i
I am having exactly the same problem - wireless = chaos - I have posted my problem and members have done their best to help but so far to no avail. I am seriously thinking of going back to 10.04 as I rely on the system to connect my various pieces of equipment, 1 x router, 2 x Humax boxes an added laptop and an NAS all connected wirelessly by wall plugs and with windows 7 virtually trouble free. It seems to me that Microsoft have gone to great lengths to make their product user friendly and Linux is now lagging behind.[/SIZE]
[SIZE=3]I have to admit that I am not a technical expert but even something like VPN is now a problem. I think that the Ubuntu gurus should concentrate on trying to make the system more user friendly particularly for newer inexperienced users.[/SIZE]

---

### Post by praseodym on 2011-09-04
Hello,

> ```
[    3.454445] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-5.ucode' failed.
[    3.455468] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[    3.455501] iwlagn 0000:03:00.0: no suitable firmware found!
```
You need the firmware package **linux-firmware** installed.

```
sudo apt-get update
sudo apt-get install linux-firmware
```

---

### Post by njwatson32 on 2011-09-04
For lack of something better to do, I tried compat again, but this time it worked.

I went to [this page]("http://linuxwireless.org/en/users/Download#Compat-wireless_release_types") and downloaded compat-wireless-2.6.tar.bz2. I then followed the instructions on that page from 'Extract' to 'Load'.

I ran (from the compat directory)
```

./scripts/driver-select iwlagn
make
sudo make install
sudo make unload
sudo modprobe iwlagn

```For some reason, it worked this time. I'm posting from my wireless connection.

EDIT: How can I mark this solved?

---

### Post by wildmanne39 on 2011-09-04
Hi, I am glad you got it working and you can mark the thread solved by using thread tools at the top of the page.
Thank you

---

