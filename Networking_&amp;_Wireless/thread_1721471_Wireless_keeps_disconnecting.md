---
title: "Wireless keeps disconnecting"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by ggirtsou on 2011-04-04
Hello,

I've just installed Ubuntu on my computer and my wireless keeps disconnecting.

I tried everything. I installed linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic

My Network controller:
Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

Thanks in advance.

---

### Post by matt_symes on 2011-04-04
Hi

> **ggirtsou said:**
> Hello,

I tried everything. I installed linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic


Karmic ? What version of Ubuntu are you running ?

Open a terminal and type

```
uname -a
cat /etc/lsb-release
```

Post back results

> 
My Network controller:
Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

Please post (case is important)

```
lspci -nnk | grep Network
```

Kind regards

---

### Post by ggirtsou on 2011-04-04
Hi,

Here's the result:
```
george@george-P5Q3-DELUXE:~$ uname -a
Linux george-P5Q3-DELUXE 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
george@george-P5Q3-DELUXE:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
george@george-P5Q3-DELUXE:~$ lspci -nnk | grep Network
george@george-P5Q3-DELUXE:~$ 

```

---

### Post by matt_symes on 2011-04-04
Hi

Is your wireless adaptor a USB adaptor ?

Kind regards

---

### Post by ggirtsou on 2011-04-04
No it's a plugged in card on computer's motherboard

---

### Post by matt_symes on 2011-04-04
Hi

I am trying to find more info about your card. I expected lspci to return something if it was a pci card. Can you post the output of...

```
sudo lshw -C network
lsusb
```

...instead. Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by ggirtsou on 2011-04-04
Now that i've rebooted my computer wireless doesn't connect at all. Posting from my phone.

Here is a screenshot of the command result: a7.sphotos.ak.fbcdn.net/hphotos-ak-snc6/196300_207272489300220_100000524123513_783329_7931848_n.jpg

---

### Post by matt_symes on 2011-04-04
Hi

> **ggirtsou said:**
> Now that i've rebooted my computer wireless doesn't connect at all. Posting from my phone.

Here is a screenshot of the command result: a7.sphotos.ak.fbcdn.net/hphotos-ak-snc6/196300_207272489300220_100000524123513_783329_7931848_n.jpg

Hmmm. This is not going well. I just looked at the URL you posted and all i get is a blank page. No screen shot.

Insert and boot off a LiveCD/USB and see if you can get wireless access from that otherwise this is going to be very hard indeed to fix.

Kind regards

---

### Post by ggirtsou on 2011-04-05
From Ubuntu Live CD, here's the output:

```

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 12
       serial: 00:22:15:89:66:72
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 14
       serial: 00:22:15:89:67:5a
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:18 memory:febf8000-febfbfff ioport:e800(size=256) memory:febc0000-febdffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:15:af:86:ec:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bgn
ubuntu@ubuntu:~$ lsusb
Bus 011 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ 

```

---

### Post by matt_symes on 2011-04-05
Hi

> linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic

I should explain a bit about backports and how they work.

You installed karmic backports to try to fix your wireless connection.

Karmic was Ubuntu 9.10 (Karmic). Your current version is Ubuntu 10.10 (Maverick). A backport from 9.10 will not fix any issues for 10.10 and could well make things worse.

You want to install backports from Ubuntu versions greater than the current version you are using as the idea of a backport is to backport bug fixes and enhancements from a newer version to an older version.

What you tried to do was backport from an older version into a newer version.

eg. A backport of Maverick (Ubuntu 10.10) into Lucid (Ubuntu 10.04).

Are you still using the Karmic backports ?

```
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:15:af:86:ec:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bgn
```

This is missing alot of information i would expect sudo lshw to return. Here is mine as an example.

```
 *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:37:55:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0400000-f040ffff
```

If this is a new install it might be quicker to backup and reinstall then trouble shoot from the new install.

Kind regards

---

