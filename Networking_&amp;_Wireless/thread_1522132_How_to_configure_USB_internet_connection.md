---
title: "How to configure USB internet connection?"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by princerameses on 2010-07-01
In Damn Small Linux?

I have a dinosaur computer I need to use for something, and there's no ethernet port. But there is USB.

On the internet box my ISP provided there's a port for a usb cable. 

But I plug it in and there's no connection. Tried Vector too. 

Is there a terminal command to make it work?

---

### Post by ieee488 on 2010-07-01
Well, in all likelihood the USB port on your dinosaur computer is 1.1, and it probably won't work with a USB 2.0 device from your ISP.

I prefer working with Puppy Linux myself. 

You might to look into USB-to-Ethernet converters that are Linux-compatible.
[http://free-electrons.com/blog/usbeth/](http://free-electrons.com/blog/usbeth/)

Is this PC a laptop? If so, if it has a PCMCIA slot, that is actually a better way to go to get internet connection.

---

### Post by princerameses on 2010-07-01
Ugh. -_-;
So there's no way to make it work? 

Would it work straight off if it was going to work?

I have a wireless usb adapter. But I've tried to use NDISwrapper countless times for 2 years and can't figure it out. 

If you or someone would want to tell me EXACTLY what to type into terminals to make it work, that would be awesome. :) Step by step leaving nothing out. I've asked several times on forums but everyone would just link me to tutorials which DO NOT HELP ME. I need step by step personal assistance. :)


By the way, I prefer Puppy too. But the dinosaur doesn't have enough RAM for it. :(

---

### Post by ieee488 on 2010-07-01
start with [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by princerameses on 2010-07-01
Yes, it is supported:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4")

(but I knew that already)

What now?

---

### Post by ieee488 on 2010-07-02
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

---

### Post by princerameses on 2010-07-03
I might try there, but I'm sure it's dead, which is why I came here.

---

### Post by flash63 on 2010-07-03
Hello,
if the Router supports this funktion you can direktly connect via USB-Cable and try to use **usbnet**.
```
sudo modprobe usbnet
ifconfig
```
(my old AVM Fritz-Box Router 7050 supported this for example)

---

### Post by princerameses on 2010-07-03
Thank you. But I found an old ethernet port from a scrap computer that is working. :D

---

