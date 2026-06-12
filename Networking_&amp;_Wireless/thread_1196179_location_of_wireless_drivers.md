---
title: "location of wireless drivers"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by toehead2 on 2009-06-24
Which directory does Ubuntu store the drivers for my wireless card? Also would a driver that worked on another version of Linux work with Ubuntu?
Thanks all!!

---

### Post by ibutho on 2009-06-24
It really depends on how the kernel is configured. The drivers will either be built into the kernel or available as kernel modules which are located in /lib/modules/2.6.x.y. A driver from another distro will work, but you can't just pluck the driver from another distro. You have to compile the driver against your Ubuntu kernel or install a newer kernel which has the drivers you need.

---

### Post by toehead2 on 2009-06-24
Thanks for the quick reply, I had wireless working in Ubuntu, then had to do a re-install, the driver that loaded worked-sort of. It would connect, then after a few seconds or minutes disconnect. So I tried to install other drivers thru guides on this forum, using NDISWrapper, which isn't working at all. Wired works great. On another flavor of Linux the driver was the same as the one Ubuntu installed except the version number appeared to be older, which worked fine, which is why I was looking for the directory. Any help anyone can give me to get it back to the proper driver would be greatly appreciated. I can supply needed info.

---

### Post by jimv on 2009-06-24
What version of Ubuntu and what kind of card? 

You can get the info for the card by typing this in a terminal:

```
sudo lspci
```

---

### Post by toehead2 on 2009-06-25
I'm running Hardy,

mike@mike-laptop:~$ sudo lspci
[sudo] password for mike: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 11)

---

