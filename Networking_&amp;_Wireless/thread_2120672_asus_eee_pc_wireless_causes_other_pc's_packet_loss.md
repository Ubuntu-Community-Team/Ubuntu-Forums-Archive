---
title: "asus eee pc wireless causes other pc's packet loss"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by samfraser on 2013-02-27
Hi all I wonder if one of you wireless guru's could help me here.  I've noticed - after complaints! That when I turn my asus netbook on, which is running ubuntu 12.10, that all other PC's on the wireless lan start getting packet loss!! This is causing a significant amount of angst as you can imagin!  Here is some cli I commands, can you see anything amiss?

lsmod | grep wl
wl                   3074773  0 
cfg80211              206797  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl

lspci | grep Network 
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
samfraser@asus:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"frasers"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 7C:4C:A5:45:F6:95   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by jack454 on 2013-02-27
I had a similar problem recently with an HP notebook. t was caused by a recent driver update. I removed bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb and replaced it with   
bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb. You can find it here. [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/]("http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/") If your system is 32 bit you need the i386 version rather than the amd64. Hope this works for you.

---

### Post by samfraser on 2013-03-07
Thanks that worked!

---

