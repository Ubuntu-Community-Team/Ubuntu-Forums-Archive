---
title: "Samsung WIS09ABGN"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by nhasian on 2009-10-26
When I bought my Samsung UN55B8000 LED TV, it came with this Samsung WIS09ABGN wifi usb 2.0 adapter.  Since I'm running ethernet to my TV, i thought I would try to use the Samsung WIS09ABGN adaptor on my Ubuntu PC.  Please note that the samsung TV uses linux so I figure there must be a way to make it work in ubuntu as well.  :)

when i run lsusb it says:

> Bus 002 Device 009: ID 04e8:2018 Samsung Electronics Co., Ltd

```
lshw -C network
```

says:
> 
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:12:fb:27:ee:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn

my NetworkManager applet calls it an "Ralink 802.11n WLAN" but I dont know if thats correct since i dont see that anywhere in the lshw description.

by the way i'm running Ubuntu 64bit Karmic Koala.  Any ideas are appreciated.  thanks!

> 
Linux ubuntutop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

---

### Post by Maximiliano on 2010-04-19
Have a Samsung Led 7000 series, and want to conect wifi with ubuntu with the usb adapter. Any idea?
Thanks

---

