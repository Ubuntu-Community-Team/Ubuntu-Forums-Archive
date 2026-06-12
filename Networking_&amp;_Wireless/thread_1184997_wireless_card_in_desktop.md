---
title: "wireless card in desktop"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by endurance001 on 2009-06-11
I'm trying to enable a wificard in a desktop how do i go about doing that??

---

### Post by superprash2003 on 2009-06-12
first lets see which wifi card you have  , post output of **lshw -C network** from the ubuntu terminal

---

### Post by kerry_s on 2009-06-12
> **superprash2003 said:**
> first lets see which wifi card you have  , post output of **lshw -C network** from the ubuntu terminal

if you don't have "**lshw**" installed you can use the standard command:
```
**lspci | grep net**
```

---

### Post by endurance001 on 2009-06-16
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


SORRY ABOUT THE LONG WAIT

---

### Post by kerry_s on 2009-06-16
looks like there's no linux driver for that netgear.
but it does seem to work with the windows divers using ndiswrapper.
[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

thats for the manual way. i would grab the gui: **sudo apt-get install ndisgtk**

---

### Post by endurance001 on 2009-06-18
Thank you Thank you Thank you !!!!! It worked !!!

---

