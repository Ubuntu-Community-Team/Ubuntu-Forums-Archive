---
title: "Wifi Card Help"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mcclunyboy on 2012-10-27
Hi,  How the hell do I get this Belkin F5D7000v3 card to work?  I have just plugged it in, driver doesn't seem to be installed but I know some ubuntu versions have it...Mine clearly doesn't..Can someone point me to a tutorial?  I have been hunting for one ...   ```
 lspci -vvnn | grep 14e4 
```  3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)

---

### Post by chili555 on 2012-10-27
Isn't this a wireless device?>  Belkin F5D7000v3 And isn't this a wired ethernet device?> Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] Let's start over. Please let us see:```
lspci -nn | grep 0280
lsb_release -d
```Thanks.

---

### Post by ahallubuntu on 2012-10-27
What version of Ubuntu are you using?

FYI, "Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express" is a wired ethernet card, not a wireless card.

According to this, your wireless card uses the Ralink rt2500pci chiset. The driver should be in the recent versions, probably since 11.10:


[http://ubuntuforums.org/showthread.php?t=1645831](http://ubuntuforums.org/showthread.php?t=1645831)
[http://wiki.debian.org/WiFi/rt2500](http://wiki.debian.org/WiFi/rt2500)

---

