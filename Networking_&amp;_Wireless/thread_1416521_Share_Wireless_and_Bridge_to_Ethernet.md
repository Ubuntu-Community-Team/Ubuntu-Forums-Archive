---
title: "Share Wireless and Bridge to Ethernet"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by WhiteHorse on 2010-02-26
Hi, I'm trying to share my ethernet via my wireless card. It doesn't work. Here is some info:

> lspci
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

> lsmod
b43, mac80211, cfg80211, ssb

I've tried everything listed in these forums but every time I run 
> sudo iwconfig wlan0 mode master

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I tried the STA drivers and get the same thing except the kernel module loaded is wl instead of b43.

Is it even possible to set this card to master mode? I can't find jack on the net. HELP!

P.S. > uname -r 
2.6.31-19-generic

---

### Post by dvlchd3 on 2010-02-26
Have you seen this?

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

Secondly, are you using the b43-fwcutter package for your wireless driver and firmware?  I believe this is the only way for Broadcom cards to support master mode.

Not sure how much help that is, but perhaps someone else may have some more specific details.  I've only ever setup my laptop (Broadcom BCM4318) as a AP in Backtrack for pentesting purposes.  This utilized the aircrack-ng suite.  You may want to look into that as an alternative.

---

### Post by WhiteHorse on 2010-02-26
All I can gather from that guide is this:
Broadcom cards support master mode using the reverse-engineered kernel driver. You need to enable (or make as a module) the Softmac wireless extensions and BCM43xx wireless driver.

I have no idea how to enable softmac extensions...

---

### Post by WhiteHorse on 2010-02-27
Hey this is really weird! I can enable an access point using airbase-ng and connect to it from other wireless devices so I'm pretty darned certain the card supports acting as an Access Point. Hell, I can do just about anything I want with the card using the aircrack-ng tools. Why can't I get network manager to do this?

What's even more strange is that airbase won't use wlan0 but will use mon0 after I run air airmon. How weird...

---

