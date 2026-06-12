---
title: "Broadcom Wireless 4306 Fail"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by pauljayd on 2011-08-11
I have finally given up on getting my Broadcom 4306 card to work with Ubuntu. I'm currently on 11.04, and have tried every ndiswrapper, download, reconfigure, restart, etc., etc, and have gone to a D-Link Air-Plus G DWL-G630 card. Period.
However, both my Windows-XP (from the dual-boot), and cd-based Linux Puppy systems have absolutely NO PROBLEM with the card. They just work.

---

### Post by gordintoronto on 2011-08-12
First, get rid of all that bad stuff. Connect with an Ethernet cable. You can go into Synaptic and search for 'b43'. There will be three firmware packages, each with a list of the cards they support in the description. Your card will be there.

---

### Post by pauljayd on 2011-08-12
I wish it were that simple. I'm a Linux/Ubuntu newbie, and don't know very much. I've tried to follow many, many threads on this problem, and have unknowable things loaded on the system by now. 
I don't know how to "get rid" of everything.
I tried the Synaptic "b43" - the b43legacy driver  is already installed.
Again, though, with Puppy and WinXP, I just boot & go.
On the Ubuntu, I just plug the pcmcia in, and it works. Not so the built-in Broadcom.
I've tried Network Manager, Wicd, etc., etc., etc.
I'm now waiting for Oneiric and will try a fresh install of that.
Thanks, anyway.

---

### Post by nm_geo on 2011-08-12
The BCM4306 is a unique chipset rev(2) uses one firmware and rev(3) uses another.. 

```
lspci -nn | grep 0280
``````
sudo lshw -C network
``````
dmesg | grep firmware
```Copy and paste results please.

---

### Post by pauljayd on 2011-08-14
Thanks for your atention to this problem.

lspci -nn | grep 0280 - response follows:

02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

sudo lshw -C network -- response follows:

  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:35:9a:c4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:3000(size=256) memory:d2007800-d20078ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:d2004000-d2005fff
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 01
       serial: 00:11:95:4a:05:ef
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.0.100 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:68000000-6800ffff     


dmesg | grep firmware -- response follows:
 
(null) - there was no response.

PaulJayD

---

### Post by nm_geo on 2011-08-14
From what I see you would need the following to make the bcm4306 (rev2) work.

```
b43-fwcutter
```

```
firmware-b43legacy-installer
```

If you go to Synaptic please read the properties info on the firmware-b43legacy-installer.  I think you will see that for rev 2 it is required.

---

### Post by pauljayd on 2011-08-14
Started Synaptic Package manager and *re-installed* both b43-fwcutter and firmware-b43legacy-installer, then re-issued the dmesg | grep firmware, and **still no response.**

What next?

PaulJayD

---

