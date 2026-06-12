---
title: "Slow Wireless Internet"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Kevinlittleton on 2009-12-23
Hi all,

I'm very new to the whole Linux/Ubuntu scene but I am really loving it so far. The only issue I've had is a weird issue with the wi fi.

I'm using Ubuntu Remix 9.10 and I had to install the proprietary driver for my wireless card. I have an HP Mini 110 and a D-Link DIR 655 wireless router. 

I was using Windows XP before and I had no troubles with the internet. Do you guys have any tricks that may help? I'm very new so troubleshooting for me is not coming very easy. :P

Thank you!

---

### Post by 00ber n00b on 2009-12-23
Why do you think it's running slow? What proof do you have that your wireless network is the culprit?

---

### Post by Kevinlittleton on 2009-12-23
> **00ber n00b said:**
> Why do you think it's running slow? What proof do you have that your wireless network is the culprit?

Well, the internet will work fine when I first start up the computer but after about 5 minutes it'll fail to load web pages. I do not get a disconnect message or anything though. It'll fail to load pages for a couple of minutes then resume and be very fast. Downloads also will stop after a while.

---

### Post by freds3251 on 2009-12-23
I have had the same issue come up for me. I will lose my wireless when using mandvd. Its right towards the end of the operation. Internet will go out. If it doesnt happen then it just hops on and off. connecting and disconnecting every other minute. Only solution for me is to resart computer then all im fine for a little while. This doesnt happen all the time, but it sure is annoying when it does. By the way im using the D-Link usb stick. Forget which model now, but anyway. I would suggest restarting if this happens to you. Hope this helps!!

---

### Post by Kevinlittleton on 2009-12-23
Is there a way to maybe reinstall the driver for the WIFI and see if that would work? I did install it a funky way and don't remember how I did it.

---

### Post by Ryantoss on 2009-12-23
> **Kevinlittleton said:**
> Hi all,

I'm very new to the whole Linux/Ubuntu scene but I am really loving it so far. The only issue I've had is a weird issue with the wi fi.

I'm using Ubuntu Remix 9.10 and I had to install the proprietary driver for my wireless card. I have an HP Mini 110 and a D-Link DIR 655 wireless router. 

I was using Windows XP before and I had no troubles with the internet. Do you guys have any tricks that may help? I'm very new so troubleshooting for me is not coming very easy. :P

Thank you!

Hello, i am new for ubuntu. However, i experienced exactly same problem as you before.

What you have to do.

1. Install official network setup from provider with help of "ndiswrapper". This one is hard one.

2. Or you can try to upgrade new kernel by using "update manager" which already included in ubuntu. This one is easier. However, upgrade new kernel sometimes result in lost in "driver" for your current sound, VGA card. You have to recompile this again.

Good luck

---

### Post by Kevinlittleton on 2009-12-23
Do you have a guide or something that will help me through that first option for "ndiswrapper".

---

### Post by Ryantoss on 2009-12-23
> **Kevinlittleton said:**
> Do you have a guide or something that will help me through that first option for "ndiswrapper".

Youtube has some man :lolflag:                               . Download ndiswrapper and officer driver setup from provider.

---

### Post by Kevinlittleton on 2009-12-23
I followed a guide on Youtube but the only problem is I can't find an .inf file for my wireless driver. 

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3979288](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3979288)

---

### Post by Kevinlittleton on 2009-12-24
Anyone?

---

### Post by Kevinlittleton on 2009-12-24
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by moore.bryan on 2010-01-05
Broadcom is notoriously "bad" with Linux, but there's hope.

Could you follow the [WifiDocs' *Wireless Trouble Shooting Guide*]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and report back?

---

