---
title: "Virgin Mobile Broadband - Alcatel X220S problems"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by purct on 2011-04-11
Hi Everyone,

Just got a new Virgin Mobile Broadband Modem and have been having some issues in Ubuntu 10.10 (Kde) :(

KnetworkManager fails to connect via the dongle.....Well more often than not!  

Firstly, I takes sometime to detect that the dongle has been plugged in.    Then I try and connect and its says failed to connect.   I looked in /var/log/syslog and I see error/warnings.

modem-manager: (Longcheer): GSM Modem /sys/device/pci0000:00/0000:00:1d.7/usb2/2-1 claimed port ttyUSBx  (x is a number between 1 and 4)

(tty/ttyUSB0): out standing support task prevents export of /sys/device/pci0000:00/0000:00:1d.7/usb2/2-1

Also seeing :  GMS connection Failed: (32)  sending command failed: 'Resource temprorarily unavailable'

I think it is failing depending on the Signal I am getting on the Dongle.   So when commuting to work - I can connect because the signal is NOT great (ie 2g for example)....but when I am at work (Central London - I can't connect - although if I connect in Windows and its full 7.2Mbps)

I found a tool sakis3g that appears to work great for connecting and general Internet(but if I use it - I can't deliver email in evolution because wants KNetworkManger to confirm that the link is up)


Any Ideas on how to resolve either the Evolution Email Problem or Make KNetworkManager work correctly?



(I would prefer to use KNetworkManager because I use it for my wireless card when I am at home!)

---

