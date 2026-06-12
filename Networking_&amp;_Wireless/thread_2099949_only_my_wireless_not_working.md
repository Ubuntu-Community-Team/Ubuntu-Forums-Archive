---
title: "only my wireless not working"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by profeta81 on 2012-12-31
Hello all,

I had an acer aspire 5742 for sometime now and wireless worked more or less ok so far.

Today I tried to connect to a wireless at my mother's place (had never tried to connect from here) but the network does not apper in the list of networks. My partner laptop is happily connected and my android phone connects with no problem...

cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux ltrojan-acer 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0487]
	Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
	Subsystem: Foxconn International, Inc. Device [105b:e040]
	Kernel driver in use: wl

```

iwconfig
```
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

usb0      no wireless extensions.

eth0      no wireless extensions.

```

rfkill list all
```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

thank you
Lorenzo

---

### Post by profeta81 on 2013-01-01
nobody??

The problem is that the wireless network from my router is not displayed on the list of available networks in the network manager, my router wireless network is the only one that doesn't come up in the list, i can see my neighbour's and I've been using the laptop pretty much everywhere

cheers
Lorenzo

---

### Post by Hadaka on 2013-01-01
Hi, power down and then restore power to your router and your computer
then try this..

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```
hope this helps.

---

