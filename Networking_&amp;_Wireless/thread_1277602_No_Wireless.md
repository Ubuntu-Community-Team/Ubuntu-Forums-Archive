---
title: "No Wireless"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by regdabs on 2009-09-28
New to this and have not been able to get wireless to work.  I have a broadcom 4321 chipset and from what I have read there is no support for this at the present time.  Also that Ndiswrapper does not work with Vista drivers.  Is this all correct and if so am i just out of luck.  I have tried all this and still nothing, Ubuntu just doesn't see my card at all.  Works fine in Vista.

---

### Post by spd106 on 2009-09-28
Have you tried the binary driver from Broadcom?

See [http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

I would have thought that someone would have a PPA of this for 9.04, but I guess there are probably some serious license restrictions.

---

### Post by t0mppa on 2009-09-28
The STA does indeed support this chipset, so you've been somewhat misinformed. It should actually be the default driver for this chip, if I'm not mistaken. Open up a terminal, run **lshw -C network** and post the results, that should clear things up a bit.

---

### Post by Ayuthia on 2009-09-28
As the others have mentioned, the card should work in Ubuntu.  You should be able to activate it by going into System->Administration->Hardware Drivers and activating the Broadcom STA option.  If it does not work, you might go into the Terminal and try the following to see if you can get wireless sites:
```
sudo modprobe -b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```

If you do get wireless sites, please do the following:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
```

---

### Post by regdabs on 2009-09-29
Thanks--things seem to be working now

---

