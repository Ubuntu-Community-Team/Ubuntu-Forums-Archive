---
title: "Internet doesn't work on MSI U130"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by juliusnkemdiche on 2010-01-09
Please help! I really want to convert over to ubuntu and use ubuntu netbook remix on my new netbook but I've had a hell of a time trying to get it to access the internet, I've tried installing drivers but I don't really know how.

My Netbook Details:

MSI U130
1.66 Intel Atom N450
1GB DDR2 Ram
Windows 7 Starter
802.11 bgn 1r1t Mini Card Wireless Adapter

Please help, Thank you

---

### Post by sanderj on 2010-01-10
If you live-boot:

Run the commands "lspci" and "lsusb" and post the output here.

Does Ubuntu offer to install extra drivers? In the plain Ubuntu, it would show a green hardware card.

---

### Post by juliusnkemdiche on 2010-01-10
> **sanderj said:**
> If you live-boot:

Run the commands "lspci" and "lsusb" and post the output here.

Does Ubuntu offer to install extra drivers? In the plain Ubuntu, it would show a green hardware card.
hey sanderj, here's what I got:

lsusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 003: ID 5986:02c1 Acer, Inc 

Bus 001 Device 002: ID 0781:5204 SanDisk Corp. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lspci:

00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge

00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller

00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)

00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by sanderj on 2010-01-10
OK, the informative part is

01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

Same problem + solution:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/95245](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/95245)

Summary: use the PPA driver described here: [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090) Make sure you click on "Technical details about this PPA": it will open and show what to do.

NB: you have to connecto to Internet to install that, so first connect a ethernet cable from you computer to your fixed ethernet.

HTH

---

