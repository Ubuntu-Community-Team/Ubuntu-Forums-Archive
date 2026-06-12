---
title: "Netgear MA111"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by polishemokid on 2006-05-09
I have a PC with ubutnu and for some reason the Netgear MA111 wireless network USB device doesnt do anything, the computer wont connect to the net using this device.  I have attempted to use winetools to install the software but that doesnt seem to work.  How can i get this wireless network setup using my MA111

---

### Post by jml on 2006-05-09
More information would be helpful.  Is the USB device listed as one of the network devices in the network manager application?  If it is, then you just have some configuration to do.  If it isn't, you will need to use the windows drivers supplied on the install CD that came with your device using an application called ndiswrapper.  Information on how to do this is located in the wireless troubleshooting wiki;

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

hope this helps.

Joe

---

### Post by az on 2006-05-10
[https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111](https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111)

---

### Post by Sensatus on 2006-05-21
I'll give the "How to" a try and report back...

However, the real issue is "Why can't Ubuntu handle this in the install sripts?"

Also, having been following Wifi + flavours of Linux for 4 years, it does seem a little overdue to have a standard (ideally GUI) means of installing/configuring wifi, including encryption, as a standard part of the distro and installation.

---

### Post by Sensatus on 2006-05-21
Follow  up as promised.

The 'how to' does not work under Dapper.

This might be because linux-wlan-ng is unavailable.

The results are the same before and after editing the various configuration files (which IMHO should be unnecessary) as suggested. 

These are:
lsusb shows the hardware as recognised as a wifi card, with a MAC address 
ifup reports wlan0 already configured
ifconfig reports wlan0 not up, when forced shows wlan0 with neither MAC address nor IP address
Networking Tools shows LO and ETH0 but no WLAN0

In conclusion, the hardware is there, the driver is loaded, but nothing results,

Ho hum

---

### Post by chrisharte on 2006-05-28
Hi,

Check this post - I fixed the same problem on my machine running breezy:
[http://ubuntuforums.org/showthread.php?t=182786](http://ubuntuforums.org/showthread.php?t=182786)

Hope that helps

Chris

---

