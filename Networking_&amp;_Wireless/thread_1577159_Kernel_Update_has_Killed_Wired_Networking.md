---
title: "Kernel Update has Killed Wired Networking"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by robertv on 2010-09-18
I updated to the latest available kernel for Kubuntu 10.04 today (2.6.32-24). When the system rebooted, it refused to connect to my wireless network. So far I have been unsuccessful in persuading it to connect. ifconfig shows the existence of the ethernet connection as eth0, and Network Manager also seems to accept the existence of the ethernet port - so why has it suddenly chosen now to stop connecting to the wired network? Any help is greatly appreciated.

---

### Post by cemilhilton on 2010-09-18
i'm having the same problem with x86-64. Windows works but Ubuntu networking does not (I have two different ethernet cards and a wireless dongle) so it is clearly Ubuntu related.

---

### Post by F.McC on 2010-09-18
I am having the same problem with x86-64, also after the kernel update this morning. I've had no luck with either wicd or network-manager. My problem is solely with wireless connection, wired is functioning as normal.

---

### Post by snowpine on 2010-09-18
You can choose the previous kernel from the GRUB boot menu; does that restore networking functionality?

---

### Post by F.McC on 2010-09-18
A previous kernel was the first thing i tried, sorry. Previously knetworkmanager would not connect at all, it now does, or at least says it does, but nothing will load. Machine has an IP, but i am not able to ping anything

I will investigate further what else was installed today.

---

### Post by cemilhilton on 2010-09-19
I too have tried using the old kernel, to no avail. Wicd also did nothing for me. Still able to access the internet via Windows.

---

### Post by PureW on 2010-09-19
Same here, my wired desktop (64bit) has no lan-connection anymore.
My laptop still has wifi and it connects to my home wlan, but wicd's tray icon is gone so I can't actually pick a wlan to connect to.

I'm not sure how to pick another kernel in when the computer is starting, could someone tell me?

EDIT: I tried booting into 2.6.32.23 instead of the new ...24 and I still don't get a lan-connection on my desktop-computer.

---

### Post by perezomail on 2010-09-19
thus-far the new kernel has not affected my desktop however cant say the same about my net-book. i should mention i don't know if this is the new kernel or just the fallacy of false cause; only since my desktop is still on line. might this be a KDE desktop issue since i had until recently only used GNOME other than KDE on the net-book and never had this issue

---

### Post by kweetniet on 2010-09-22
> **PureW said:**
> Same here, my wired desktop (64bit) has no lan-connection anymore.
My laptop still has wifi and it connects to my home wlan, but wicd's tray icon is gone so I can't actually pick a wlan to connect to.
 
I'm not sure how to pick another kernel in when the computer is starting, could someone tell me?
 
EDIT: I tried booting into 2.6.32.23 instead of the new ...24 and I still don't get a lan-connection on my desktop-computer.
 
netbook
same problems :
no lan 
no wifi 
no knetworkmanager
no vpn
 
tried old kernel 23 and 22

---

