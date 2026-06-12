---
title: "sta in oneiric 11.10 not working"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by tongsengpakronilezat on 2011-11-15
just upgraded my comp to ubuntu 11.10 and my wifi is not working. 
following are my data :

ubuntu 11.10 Oneiric Ocelot
3.0.0-12-generic i686

lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

In 'the list' it is supported by b43 drivers, but it's also supported by wl drivers ( or STA ).

lsmod | grep wl :
wl                   2646601  0 
lib80211               14570  1 wl

In Settings>Hardware>AdditionalDrivers, i can see : 
Broadcom STA wireless driver
    Tested by the Ubuntu developers
    License : Proprietary
    This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

    This driver is activated and currently in use.

This seems to installed automatically by the upgrade to Oneiric. Tried to shut down and up a few times, but still fail. So, i tried to blacklist, but still failed :

sudo echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied

What else should  i do ? Please help . . .

---

