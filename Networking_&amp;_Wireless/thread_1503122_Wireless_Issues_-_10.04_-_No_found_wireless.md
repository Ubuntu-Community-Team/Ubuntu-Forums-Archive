---
title: "Wireless Issues - 10.04 - No found wireless"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by sebdavies1989 on 2010-06-06
Hello.

Ive installed 10.04 on my laptop and notebook.

It works perfectly on laptop.

On notebook the problem is it finds no Wireless network and just says disconnected.

I have no idea how to connect it, I tried reinstalling Ubuntu but no luck.

I tried looking it up on internet but no luck in finding help.

Any ideas?

Its an MSI U130. The wireless is defently turned on. Thanks for youre time.

---

### Post by purelinuxuser on 2010-06-06
Hello!  In order for us to help you, we'll need some debug information.  Open a Terminal (Applications > Accessories > Terminal) and type the following commands:
```
lspci
lshw -c network
iwconfig
```
Since you don't have an Internet connection and can't copy and paste to a reply, you can copy and paste to a text file and save it on a flash drive ;)

---

### Post by sebdavies1989 on 2010-06-07
Hey, ive currently got a wireless device in the usb so thats how im currently connected. This is what it came up with when i typed that in the terminal part. Thing is I love this Ubuntu but it just needs to work lol!

> 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
sebdavies1989@sebdavies1989:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:14:5f:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:e000(size=256) memory:e0010000-e0010fff(prefetchable) memory:e0000000-e000ffff(prefetchable) memory:fe800000-fe81ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:12:17:83:f0:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.69 multicast=yes wireless=IEEE 802.11bg
sebdavies1989@sebdavies1989:~$ iwconfig

:popcorn:

---

### Post by sebdavies1989 on 2010-06-07
And this is what it says when I turn the wireless on at by pressing FN and F11

> sebdavies1989@sebdavies1989:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
sebdavies1989@sebdavies1989:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:14:5f:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:e000(size=256) memory:e0010000-e0010fff(prefetchable) memory:e0000000-e000ffff(prefetchable) memory:fe800000-fe81ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:12:17:83:f0:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.69 multicast=yes wireless=IEEE 802.11bg
sebdavies1989@sebdavies1989:~$ iwconfig

:KS

---

### Post by purelinuxuser on 2010-06-07
```
sebdavies1989@sebdavies1989:~$ lshw -c network
WARNING: you should run this program as super-user.
  ***-network DISABLED      **
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0  multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
```

That is odd, the network interface is disabled!  I assume Fn+F11 is the wireless enable/disable key.  Have you tried looking for a physical switch around your laptop?

---

### Post by sebdavies1989 on 2010-06-07
It is the enable and disable key but no hard buttons for it. It worked with windows 7 and I even had Jolicloud (which i think is linux based) part patition before i just put Ubuntu 10.04 as only OS. Even if you dont know the solution thanks for the time for reading! :)

---

### Post by purelinuxuser on 2010-06-07
Okay, I don't REALLY know what's going on, but I searched and found a bug report on this issue.  The workaround posted was to add packages from this PPA: [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090").  Just follow the instructions on adding the PPA to your software sources list, and then update your system via Update Manager as usual.

Source: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

---

### Post by sebdavies1989 on 2011-03-11
an I just say that even though I couldn't find a way to fix this after a few months, and Ubuntu updates it did fix this issue!

---

