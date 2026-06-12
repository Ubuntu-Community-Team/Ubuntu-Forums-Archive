---
title: "NetworkManager .. hazardous?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by A_Fiachra on 2009-09-28
I've been griping and grunting about my Dell Laptop and it's Broadcom Wireless card 

```

$ sudo lspci | grep -i network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```For absolutely no reason I can imagine, my wireless interface went down, I poked around:

```

$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:f9:80:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.102 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:56:59:35
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s


$ ls -l /lib/modules/`uname -r`/volatile/
total 2192
-rw-r--r-- 1 root root  216975 2009-09-28 17:19 ath_hal.ko
-rw-r--r-- 1 root root  124940 2009-09-28 17:19 ath_pci.ko
-rw-r--r-- 1 root root   18405 2009-09-28 17:19 ath_rate_amrr.ko
-rw-r--r-- 1 root root   25692 2009-09-28 17:19 ath_rate_minstrel.ko
-rw-r--r-- 1 root root   17528 2009-09-28 17:19 ath_rate_onoe.ko
-rw-r--r-- 1 root root   24120 2009-09-28 17:19 ath_rate_sample.ko
-rw-r--r-- 1 root root   15221 2009-09-28 17:19 wlan_acl.ko
-rw-r--r-- 1 root root   18459 2009-09-28 17:19 wlan_ccmp.ko
-rw-r--r-- 1 root root  247465 2009-09-28 17:19 wlan.ko
-rw-r--r-- 1 root root   16267 2009-09-28 17:19 wlan_scan_ap.ko
-rw-r--r-- 1 root root   26193 2009-09-28 17:19 wlan_scan_sta.ko
-rw-r--r-- 1 root root   22923 2009-09-28 17:19 wlan_tkip.ko
-rw-r--r-- 1 root root   17099 2009-09-28 17:19 wlan_wep.ko
-rw-r--r-- 1 root root   11249 2009-09-28 17:19 wlan_xauth.ko
-rw-r--r-- 1 root root 1381735 2009-09-28 17:19 wl.ko

```
-rw-r--r-- 1 root root 1381735 2009-09-28 17:19 wl.ko !!!!!!!!!!!!???????????

I know where I was at 4:19 today and I was not installing anything, running anything as root ... so, what's with the timestamps on the files in the volatile directory??

A little more investigation:

```

$ dmesg | grep -e b43 -e wl
[   10.660323] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.662586] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.662600] wl 0000:0c:00.0: setting latency timer to 64


$ lsmod | grep -e b43 -e ssb -e wl
wl                   1281364  0
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl


```So --- nothing unusual there -- same module's been loaded all day, but stopped working?

Did a little search in the threads and found this [Gem]("http://ubuntuforums.org/showthread.php?t=1056446&highlight=wicd").

```

sudo apt-get install wicd


```
All I had to was uninstall NetworkManager (IMO a terrible application!!!!!!!!!!) and use Wicd instead -- the network reappeared, I added my WPA passphrase, and I am running wireless now.

So -- my question for Ubuntu users:  Is NetworkManager hazardous?

---

### Post by t0mppa on 2009-09-28
Perhaps not hazardous, but its development history consists of a bunch of odd choices along the way. But the real beauty of Linux world is that you can choose what software you run freely & legally and vote with your feet. WICD is far from perfect either, one of the flaws being its design of only supporting one connection at a time and you cannot connect though wired & wireless at the same time for example.

Bottom line being, if you really want to things to work your way all the time, you'll configure your connections manually without a manager of any sort, then you can only blame yourself, when the sh!t hits the fan. ;)

Disclaimer: I do use Network Manager on two Ubuntu machines and WICD on one KUbuntu laptop, so by no means meant to flame them pointlessly.

---

### Post by A_Fiachra on 2009-09-28
> **t0mppa said:**
> 

...

Bottom line being, if you really want to things to work your way all the time, you'll configure your connections manually without a manager of any sort, then you can only blame yourself, when the sh!t hits the fan. ;)

...

Well, that's true.

However, apps that alter root owned files without asking are generally a bad thing.

Perhaps wicd has the same basic flaw .. but after days of fiddling with this laptop to get wireless working removing NetworkManager instantly fixed my problem.

Hopefully this is a permanent solution.

---

