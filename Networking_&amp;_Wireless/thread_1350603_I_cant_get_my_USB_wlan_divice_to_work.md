---
title: "I cant get my USB wlan divice to work"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by steff_p on 2009-12-09
Hi!

Im an Ubuntu newbie and I cant install/get my USB wlan device to work.
I have a Konig usb 150 wlan dongle. I got it to work in windows but not on ubuntu 9.04. It came with a cd with an exe.file wich worked in windows. I tryed using wine but it didnt work 

please help me!

/stefan

---

### Post by gordintoronto on 2009-12-09
Wine is for applications, not drivers.

You can search the forums for "ndiswrapper" to see how to use the Windows driver, but maybe you don't need that.

When you say you "can't get it to work," it doesn't give a person any useful information for helping you.  You will get better help when you say, "I did XXX and the result was YYY instead of ZZZ."  

You are new, so perhaps you don't know that in many cases, a network adapter "just works," when you right-click on network manager (near the date and time), and select "edit connections."  If the network adapter is not recognized, Network Manager might not be there.

Here's something useful you can do: run Accessories/Terminal, and enter the command lsusb, which will display the exact model of the USB device.  Also, tell us what version of Ubuntu you are using.

Good luck!

---

