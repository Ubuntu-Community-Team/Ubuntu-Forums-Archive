---
title: "Belkin Wireless Dropping"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by LakesideLoafer on 2011-02-12
Having a problem with my Belkin wireless adapter when trying to stream music to my Pinnacle Soundbridge.

The network connection is usually rock steady but drops anywhere between and few second and a few minutes after streaming music. Network manager still shows the connection to my home network as active but it is not. The connection comes back when I unplug the dongle and plug it back in.

I found the following message repeated in the syslog

phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110

Only thing I have noticed is that it refers to rt2x00 when I had thought it used the rt73usb driver.

Had the PC and the Soundbridge for a number of years without any problems but I did recently have to reinstall Ubuntu from scratch. Currently running Ubuntu 10.10

Any help appreciated.

Thanks

---

### Post by Dark_Stang on 2011-02-12
Let's find out what's really inside that usb hub. Run the following command with the dongle plugged in and paste the output from the dongle here.
```
lsusb
```

---

### Post by LakesideLoafer on 2011-02-12
I get the following:

```

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 008: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 005: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Dark_Stang on 2011-02-12
> **LakesideLoafer said:**
> ```

Bus 001 Device 008: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]

```

So the card is actually a Ralink card, which I'm not familiar with. This thread suggests blacklisting some other drivers, may be worth a shot.
[http://ubuntuforums.org/showthread.php?t=1475928](http://ubuntuforums.org/showthread.php?t=1475928)

---

### Post by LakesideLoafer on 2011-02-12
Thanks, I'll give that a go and post how I get on.

---

