---
title: "[SOLVED] Dell 1500n wireless mini card help (new to Linux)"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Toady00 on 2009-01-04
Sorry for the length on this post but I figure more is better.

Machine - Dell Inspiron e1705
Wireless Card - Dell 1500n wireless mini card
Chipset - Broadcom BCM4328 802.11a/b/g/n (rev 01)
ifconifg returns only eth0 and lo
iwconfig returns lo eth0 and pan0 all say no wireless extensions.
OS - Ubuntu 8.10 32 bit

I've decided to give Linux a try. Installed Ubuntu on laptop and can't get wireless working. I donwloaded the ndiswrapper by going to Applications>Add/Remove and typing in ndiswrapper. Windows Wireless Driver shows up and that is what I downloaded. I downloaded the driver from dell's website and extracted the .inf file. I ran the GUI for ndiswrapper and pointed it to the .inf file and nothing happened. Restarted and still nothing. 

I found a how to at [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29). When I got down to Step 5 I started getting errors on "Make the driver with the commands "make distclean", "make", and "make install"" Everything kind of goes blurry after that due to frustration.

I'm really liking Ubuntu so far, but wifi is a deal breaker and I'll have to go back to Brand X. I also have a Belkin N1 wireless usb adapter that I could use but I'd rather use the built in wireless. The Belkin is chipset F5D8051. If all else fails does anyone know of a 802.11n card that will work with Ubuntu 8.10 without any issues?

---

### Post by Ayuthia on 2009-01-05
You might first try and see if you can get the Broadcom STA module working first:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

### Post by superprash2003 on 2009-01-05
have you looked at system->admin->hardware drivers

---

### Post by Toady00 on 2009-01-05
Thanks for the help. I happened to come across another post where they reinstalled ubuntu and selected the sta driver and all was well. I tried and it connected.

---

### Post by superprash2003 on 2009-01-06
cool.. please mark thread as SOLVED under thread tools

---

