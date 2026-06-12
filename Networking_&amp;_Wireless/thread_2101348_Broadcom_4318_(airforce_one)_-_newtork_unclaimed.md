---
title: "Broadcom 4318 (airforce one) - newtork unclaimed"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by bazsound on 2013-01-04
Ok so ive just stuck a broadcom card in my ubuntu 12.10 machine and have spent the last few hours going through posts here and there, on these forums, on wikis.

from what i have read, it should be just a case of installing a few packages and it gets recognised and works.


lspci

```
01:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

chipset is supported. the b34 driver is loaded but there is 2 strange errors

```

```[ 1918.093061] lib80211_crypt: unregistered algorithm 'NULL'
[ 1935.231038] ssb: Failed to register PCI version of SSB with error -12
[ 1935.231079] b43-pci-bridge: probe of 0000:01:0a.0 failed with error -12
[ 1935.236476] cfg80211: Calling CRDA to update world regulatory domain
[ 1935.249446] cfg80211: World regulatory domain updated:
[ 1935.249452] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1935.249455] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1935.249457] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1935.249459] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1935.249461] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1935.249463] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1935.263335] Broadcom 43xx driver loaded [ Features: PNL ]

if i  sudo lshw -C network

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 56:38:23:1f:f4:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.201 link=yes multicast=yes

```

Network is unclaimed which suggests no driver.


Any one have any ideas?

---

### Post by bazsound on 2013-01-04
>  Broadcom 43xx driver loaded [ Features: PNL ]
[ 4196.338114] lib80211_crypt: unregistered algorithm 'NULL'
[ 4201.000046] ssb: PCI-ID not in fallback list
[ 4201.000053] ssb: Found chip with id 0x0000, rev 0x02 and package 0x00
[ 4201.000055] ssb: CHIPID not in nrcores fallback list
[ 4201.000061] ssb: Core 0 found: UNKNOWN (cc 0x8FF, rev 0x7F, vendor 0xFFFF)
[ 4201.011741] ssb: WARNING: Using fallback SPROM failed (err -2)
[ 4201.011746] ssb: WARNING: Invalid SPROM CRC (corrupt SPROM)
[ 4201.011748] ssb: Unsupported SPROM revision 255 detected. Will extract v1
[ 4201.019129] ssb: Sonics Silicon Backplane found on PCI device 0000:01:0a.0
[ 4201.023473] cfg80211: Calling CRDA to update world regulatory domain
[ 4201.035512] Broadcom 43xx driver loaded [ Features: PNL ]
[ 4201.047920] cfg80211: World regulatory domain updated:
[ 4201.047926] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4201.047929] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4201.047931] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4201.047933] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4201.047936] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4201.047938] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


tried a few more things, reinstalling the source and firmware packages, 

now i have different error.

This card has came out of another PC running windows xp , so its a working card. the card also has ASUS on it

---

### Post by bazsound on 2013-01-04
I managed to get the wireless card to work using instructions from this link

[http://linux-bsd-sharing.blogspot.co.uk/2012/03/howto-enabling-broadcom-bcm4318.html](http://linux-bsd-sharing.blogspot.co.uk/2012/03/howto-enabling-broadcom-bcm4318.html)

> $ sudo apt-get install b43-fwcutter
$ wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
$ tar xf broadcom-wl-4.150.10.5.tar.bz2
$ cd broadcom-wl-4.150.10.5/driver/
$ sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
$ sudo modprobe b43
$ sudo echo "b43" >> /etc/modules

the last line however, gave me permision dennied even when using sudo.

---

### Post by bkratz on 2013-01-04
> **bazsound said:**
> I managed to get the wireless card to work using instructions from this link

[http://linux-bsd-sharing.blogspot.co.uk/2012/03/howto-enabling-broadcom-bcm4318.html](http://linux-bsd-sharing.blogspot.co.uk/2012/03/howto-enabling-broadcom-bcm4318.html)



the last line however, gave me permision dennied even when using sudo.




If your wireless works after a reboot, don't worry about the last command. If not, perhaps try it this way


```
sudo su
echo b43 >> /etc/modules
exit

```

---

### Post by bazsound on 2013-01-05
sweet this is now solved :D

---

### Post by bkratz on 2013-01-05
> **bazsound said:**
> sweet this is now solved :D



Glad it worked out for you. Congratulations!

---

