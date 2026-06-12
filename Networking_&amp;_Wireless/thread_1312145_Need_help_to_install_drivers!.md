---
title: "Need help to install drivers!"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by dudekaz1 on 2009-11-02
EDIT:my main problem is on the third post. plese look there if you cant help with it first post
 
hello,
 
i am a new linux user btw
 
i have intalled nswrapper just fine through add/remove programs.
i have the windows drivers for my wireless (broadcom BCM5787M) when it starts up it says " Unable to see if hardware is present."
 
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
Subsystem: Device f7a8:2041
Flags: fast devsel, IRQ 18
Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [48] Power Management version 3
Capabilities: [50] Vital Product Data <?>
Capabilities: [58] Vendor Specific Information <?>
Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [d0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [13c] Virtual Channel <?>
Capabilities: [160] Device Serial Number c3-5c-94-fe-ff-25-1c-00
Capabilities: [16c] Power Budgeting <?>
Kernel modules: tg3
 
 
i did find some linux drivers for it (i would much rather go with the linux drivers)
here is the link where i found them 
 
[http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)
 
 
If someone could please tell how to install them i would be very happy :D
 
i useing ubuntu 9.04(jaunty)
Kernal linux 2.6.28-16generic
GNOME 2.26.1
 
(i am just about to upgrade to the new version 9.10 but i need to have wireless before i can do this)

---

### Post by unamanic on 2009-11-02
BCM5787 is a wired Ethernet controller.

please do a:
```

lspci |grep -i net

```

---

### Post by dudekaz1 on 2009-11-02
BCM5787**M** the m stands for mobile

i tired that command i had no idea what to do....i just need to know how to install some packages for the wireless drivers I got.

 tg3-3.99k.tar.gz
tg3-3.99k-1.src.rpm
tg3_sup-3.99k-ISO.tar.gz

im asumming once i install these drivers it will work.....right:(

---

### Post by dudekaz1 on 2009-11-02
bump

---

### Post by dudekaz1 on 2009-11-03
so....the ubuntu community can't evan tell me how to install these files posted above through the termnal....yea, very helpful -_-

---

### Post by dudekaz1 on 2009-11-03
i will not rest untill an answer is given

---

### Post by dudekaz1 on 2009-11-03
.

---

### Post by dudekaz1 on 2009-11-03
=(

---

### Post by keiser_soze on 2009-11-03
I just install 2.6.31-12 kernel and happy end :) This is the link:

[http://people.canonical.com/~apw/lp386468-karmic/](http://people.canonical.com/~apw/lp386468-karmic/)

---

