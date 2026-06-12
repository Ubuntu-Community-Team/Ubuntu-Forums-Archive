---
title: "Linksys USB1000 in Ubuntu 10.04"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by Jofarmer on 2010-08-20
Hello all!

I just bought a Linksys USB1000 Gigabit Ethernet USB2.0 adaptor for my Panasonic CF-W5 only capable of 10/100TX.

I plugged it in and it was instantly recognised and worked like a charm - just only with 100MBit :-( I rebooted into WinXP (which I keep only for situations like these), installed the official driver and utility, reconnected it and voila: GBit!

I only found [this thread]("http://ubuntuforums.org/showthread.php?t=407823"), which actually was the main reason for buying this specific adaptor in the first place.

I was hoping that considering the post was over three years old I would not have to bother with ndiswrapper.

Will I have to?

I would really appreciate any suggestions.

---

### Post by Jofarmer on 2010-08-22
By now I installed the Windows driver with ndisgtk, but still no BGit speeds. I am not sure that Ubuntu uses the Windows driver though. How could I find that out and better yet, make sure it does?

---

### Post by Jofarmer on 2010-08-23
Well, I tried blacklisting asix but even though it seems like the ndiswrapper driver claimed the card solely for itself,```
$ lshw -C Network
[...]
*-network
       description: Ethernet interface
       physical id: 3
       logical name: wlan1
       serial: 00:12:17:f2:34:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+ax88178 
driverversion=1.55+USB,10/14/2004, 1.4.3.41 multicast=yes

``` still asix seems to get loaded: ```
$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it 
will be ignored in a future release.
ax88178 : driver installed
	device (**1737:0039**) present (alternate driver: asix)
```The file /etc/modprobe.d/ndiswrapper just has this```
alias usb:v0B95p1780d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v14EApAB11d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v**1737p0039**d*dc*dsc*dp*ic*isc*ip* ndiswrapper
```And after all that I still get only the 100MBit LED to light up and now (with asix blacklisted and ndiswrapper not really working) not successful connection.```
$ depmod -n | grep alias | grep -v ':' | grep -i asix
```returned nothing.

---

