---
title: "DLink DWL 520+ not appearing as an ethernet adaptor"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by Skree on 2011-09-21
Have recently installed Ubuntu 11.04 on a self built machine that was running Windows XP.  Mostly smoothly installed, but the wireless PCI card in the machine isn't recognised by Ubuntu it seems.

It's a D-Link DWL 520+, which should apparently 'just work'.  

lspci shows a 'Network Controller', ```
'Texas Instruments ACX 100 22Mbps Wireless Interface [104c:8400]'
```

but ifconfig gives only eth0 and lo, the ethernet adaptor and local loopback respectively, and iwconfig shows that neither have 'wireless extensions'.  lsmod shows no wireless modules.

Hope this is enough info to get started with!  

Many thanks in advance for your help.

---

### Post by chili555 on 2011-09-21
The fact that your wireless device is described as ethernet or network or wireless or frypan is meaningless. I also doubt that any reliable source reports that an ACX100 device works out of the box in 11.04.

It is reported to work with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520](http://ubuntuforums.org/showthread.php?t=1341794&highlight=d-link+dwl-g520)

I will be glad to assist you if you need more guidance than the link I've given you.

---

### Post by laluz on 2012-05-25
There are three editions of this card with different chipsets. If you are lucky than your problem is just that the driver for this card is blacklisted in 12.04:
/etc/modprobe.d/blacklist.conf

blacklist prism54

so just comment out this line and reboot.

---

