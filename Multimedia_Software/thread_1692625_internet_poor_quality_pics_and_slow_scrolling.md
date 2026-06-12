---
title: "internet poor quality pics and slow scrolling"
date: 2011-02-21
forum: Multimedia Software
---

### Post by Donnax on 2011-02-21
hi guys! i`m super new to this whole linux thing and i have to say that i like it, and it seems easy enough for me. My brother put it on my lap cos it wanted me to forget about windows, but he`s away and cant help!:KS
i`ve just installed the os and a few utilities, the video seemed to be ok, i can watch movies and the desktop resolution and colours seem to be ok!:p 
 but... once i surf the internet it`s another story, the pics are really poor quality, the words too, pixelated, and some online videos seemed to be slow and not perfect anyway and even the internet up and down scrolling becomes clumsy and slow when theres a few pics. :(
i`ve check if the adobe flash is on and it well is..

ex: the ubuntu logo on the top of this very page is reeeeally bad i can see the pixels of it so well.
How do i fix that? s there any plugin for firefox or something?
thanks:popcorn:
Donna

---

### Post by Donnax on 2011-02-21
come boys there must be some geek that knows how to deal with a internet graphics...
cheers

---

### Post by inobe on 2011-02-21
open terminal, type

```
lspci
```

hit enter.

copy and paste the output on next post.

sounds like some video card issue.

---

### Post by Donnax on 2011-02-21
thanks for your reply, here`s the details

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
:o

---

### Post by kelver69 on 2011-02-21
Try this...

Ubuntu 10.10 out-of-the-box comes with ipv6 enabled.  This slows Firefox to a painful crawl.  Disable it by typing **about:config** in the Firefox location bar (the little window where you would type in a URL). Click on the "I'll be careful, I promise" button and scroll down the list until you find the entry for **network.dns.disableIpv6**. Double-click on that line of text. It will turn it bold and change the value from "false" to "**true**."

---

### Post by Donnax on 2011-02-21
thanks a lot for that, ive just done it...
but what about the quality of the pics and logo ? they are really **** i promise sometimes i cant read the small words cos of the pixels, r huge... just internet though, the desktop and rest are absolutely fine!
should i try to install the new firefok 4? will it change anything?
thanks

---

### Post by kelver69 on 2011-02-22
This won't likely have anything to do with your problem, but go to:  SYSTEM >> ADMINISTRATION >> SYNAPTIC PACKAGE MANAGER  

Make sure **ubuntu-restricted-extras** is installed.

---

### Post by kelver69 on 2011-02-22
I wonder if you installed a different web browser if you would have the same problem?  Maybe try Chromium: it's in Synaptic Package Mgr.

PS... which Ubuntu are you using?

---

