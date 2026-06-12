---
title: "Netgear wg111 V2 Driver"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by coolercooler on 2009-05-09
When I recently had to reinstall ubuntu, I lost the driver that worked for me for netgear wg111 v2, I looked everywhere but couldn't  fined it, tried the netgear forums and reading some posts the attitude of some mods is appalling. 

If you are thinking of buying a new adepter the best solution would be to avoid netgear, but if you like me however find yourself having one already, and you want to move from windows and try linux use this one I found after every difficulty.

Even if you have the driver working which came with ubuntu, but you card is running a little hot try this driver with Ndiswrapper.

The driver that came with ubuntu had signal level of 21 dbm, and I had constant disconnects if it worked at all, and adapter was quite hot.

with this driver the signal jumped up to 71 dbm, only I had to add static ip and wireless ssid and wep key in the interfaces file, otherwise I couldn't connect.

This is my device id
```
 ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) 
```

My contribution.

---

### Post by RedSingularity on 2009-05-09
What does your lsusb look like in terminal??

---

### Post by coolercooler on 2009-05-09
> **Shadow121 said:**
> What does your lsusb look like in terminal??

Am not sure that I understand, the lsusb for that device is included in the above, however if you want to see the full list of devices, it's as follows.

#lsusb
```

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0618:8302 MacAlly 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by Jose Catre-Vandis on 2009-05-09
See here
[http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/](http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/)

---

### Post by coolercooler on 2009-05-11
> **Jose Catre-Vandis said:**
> See here
[http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/](http://bimma.me.uk/2009/03/29/netgear-wg111v2-wireless-usb-adapter-on-ubuntu-810/)

That does not work for me, link quality is zero.

---

