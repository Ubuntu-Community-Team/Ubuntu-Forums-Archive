---
title: "Netgear WNDA3100v2 won't  connect to a secured networks"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by Nocaix on 2011-04-03
Hey, I'm having some problem getting my Netgear WNDA3100v2 wireless USB adapter to connect to my secured network.  I have installed the drivers successfully using ndiswrapper and have disabled the default drivers.  If I try to connect to an unsecured network, it works perfectly; however, any kind of secured network (I tried WEP, WPA, and WPA2) doesn't seem to work.

I'm running Ubuntu 10.10 32bit.     Router is Netgear WNDR3400.

If anyone can help out at all it would be great.  :P

---

### Post by tygsxr on 2011-06-15
Same problem here... Driving me nuts.

---

### Post by mheizer on 2011-08-23
Having a similar problem here.  I installed 10.04, the wnda3100v2 adapter did not work at all.  Then installed the windows drivers packages with sys and ini file, still no dice.  I then did an upgrade to 11.04, now the adapter works.  But will not connect to the wndr3400 with wpa.  Oddly enough it will connect to the routers guest network, but does not resolve any ip addresses.  And it does connect to the Verizon fios wireless g router in my basement, and the buffalo draft nrouter on the opposite side of the house, which are both weak signals to the 2nd floor.  Stumped.

---

### Post by sidzen on 2011-08-23
> **Nocaix said:**
> Hey, I'm having some problem getting my Netgear WNDA3100v2 wireless USB adapter to connect to my secured network.  I have installed the drivers successfully using ndiswrapper and have disabled the default drivers.  If I try to connect to an unsecured network, it works perfectly; however, any kind of secured network (I tried WEP, WPA, and WPA2) doesn't seem to work.

I'm running Ubuntu 10.10 32bit.     Router is Netgear WNDR3400.

If anyone can help out at all it would be great.  :P

 If I remember correctly, the tech I called said to logon to [www.routerlogin.net]("http://www.routerlogin.net"), go to Backup Settings, and hit "Revert to factory default settings" and start over before trying to make changes.  

Also, is *ceni* available in ubuntu repos?  I use with a true Debian distro and it works very well.

Could not get this router to work wireless with Win7 on Mom's PC, but works fine with antiX and *ceni* scans it in no problem.

---

### Post by praseodym on 2011-08-23
Hello @all,

Broadcom-Chip-based USB-devices dont work with native Linux-drivers. They have to be used with ndiswrapper. Driver for 32 and 64 bit attached.

See [here]("http://wiki.ubuntuusers.de/WLAN/Karten/Netgear?highlight=netgear"). Its the driver from that link.

Edit: Draft-N doesn't work

---

