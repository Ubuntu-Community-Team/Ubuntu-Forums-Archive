---
title: "Ralink RT3071 Wireless Adapter"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by gsaggior on 2011-05-04
After upgrading to Ubuntu 10.10 my RALink Chispet based USB adapter stopped to work. 

I got inspired by other threads:

[http://ubuntuforums.org/showthread.php?t=1690402&highlight=ralink+usb+drivers](http://ubuntuforums.org/showthread.php?t=1690402&highlight=ralink+usb+drivers)

By simply adding the following lines to the /etc/modprobe.d/blacklist.conf , everything now work fine:

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870


:guitar:



Then reboot the PC

Cheers

---

