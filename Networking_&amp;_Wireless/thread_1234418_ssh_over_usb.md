---
title: "ssh over usb??"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by freakinjonathan on 2009-08-07
I have a small linux based device without an ethernet port. The only thing i have to work with is two usb ports. People have successfully ssh-ed into the device before with usb network adapters. Googling the subject gives a ton of results about people using ssh over usb for their ipod/iphone. Is there anyway to do that linux to linux??

---

### Post by philcamlin on 2009-08-07
do you mean ssh into their devices?
yes you need a router / wireless network and a device :)
try putty

```
sudo apt-get install putty
```

---

### Post by AliTabuger7 on 2009-08-07
You can set up your USB to function as if they were ethernet.

[http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/)

Thats the basic idea of how to get it to work as a network. The rest should be familiar.

---

### Post by freakinjonathan on 2009-08-08
thanks guys. I'm not sure if putty would work unless you could connect to it via usb. Looks like even a usb connection would require me to buy some new hardware. A special host to host usb cable which is apparently different than the normal. Thanks anyway guys.

---

