---
title: "WiFi running poorly after mobile broadband installed"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by Quorlia on 2011-06-25
Hi,

I recently was without landline broadband for a while so I bought a Three ZTE MF112 mobile broadband dongle.  I got it working under linux with usb-modeswitch and adding the following in /etc/udev/rules.d/zte_eject.rules

```
SYSFS{idVendor}==”19d2&#8243;, SYSFS{idProduct}==”0103&#8243;, RUN+=”/usr/bin/eject %k”, OPTIONS+=”last_rule”
```

However now my wireless network barely functions (with or without the dongle inserted).  If I boot into Windows everything runs fine but under linux any sort of network activity fails or takes so long as to be unusable, including pinging the wireless router itself!  There is nothing apparently wrong with the router as the laptop connects to it perfectly and connecting to an alternative router is also slow.  The computer does seem to be able to connect to the network in the first place correctly as we use DHCP and it acquires an IP address and the correct DNS and gateway settings.

The wireless card reports as an Atheros AR5007EG under Windows and seems to be using the athr5k driver under linux.

I think it must be some sort of clash between the dongle and the wireless card, but I am at a loss as to where to start troubleshooting.  Please help me!

I've attached the output of commands as required by: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681).

---

