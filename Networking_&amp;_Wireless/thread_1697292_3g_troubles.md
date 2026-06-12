---
title: "3g troubles"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by steviefordi on 2011-02-28
Ok, I give up, I'm out of my depth and need some help. I purchased a 3g dongle from the network "3" in the uk to get an internet connection on my 10.04 installation.

I boot up with the dongle inserted and lsusb reports this:
```
Bus 002 Device 003: ID 19d2:0103 ONDA Communication S.p.A.
```

I eject the device, and after a few moments lsusb reports this:
```
Bus 002 Device 004: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
```

dmesg shows us what has happened:
```
dmesg | grep usb
[   73.859776] USB Serial support registered for GSM modem (1-port)
[   73.859967] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[   73.860042] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[   73.860141] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[   73.860156] usbcore: registered new interface driver option

```

All seems ok, and I can now surf the net. So what's the problem?

Many sites/webpages just won't load, most notably [www.gumtree.com]("http://www.gumtree.com").

This may of course be a problem with the option driver. I also have a theory that the driver may be using the wrong port - udevadm says /dev/ttyUSB2 is the modem device node, but according to dmesg (above) there are 3 modem ports attached to device nodes /dev/ttyUSB0 - ttyUSB2.

Any help on this would be appreciated, but I'd really like to know if I can test the other ports and how?

B.T.W - Sites that dont' work through the 3g dongle work fine when connecting via other means.

---

### Post by GeorgeVita on 2011-03-14
> **steviefordi said:**
> All seems ok, and I can now surf the net. So what's the problem?
Many sites/webpages just won't load, most notably [www.gumtree.com]("http://www.gumtree.com").
...udevadm says **/dev/ttyUSB2** is the modem device node, but according to dmesg (above) there are 3 modem ports attached to device nodes /dev/ttyUSB0 - ttyUSB2.
Hi **steviefordi**,
for a ZTE MF636 the correct modem port is /dev/ttyUSB2 (when it is attached as 0-1-2) so everything seems to be OK. I am using the same modem. After succeeding the connection I tried your link and loads fine! So the problem may be at your connection speed (some heavy pages 'cannot wait'). 3G modems can connect using GPRS also. You can check connection speed looking the color of the blinking led while conected. Blue and light blue is the 'fast' connection.

Wait for the 'blue' led before clicking 'provider' to connect.

Regards,
George

---

### Post by steviefordi on 2011-03-14
Thanks for the reply. I got around this problem by changing the APN from 3internet (GNOME Network Manager default) to three.co.uk. 

Maybe it needed to be three.co.uk because I have a pay-as-you-go dongle rather than a contract.

All sites now seem to function as expected but 3g can be painfully slow, especially since I've been spoiled in the last few years using to a fibre optic connection!

cheers
Steve.

---

