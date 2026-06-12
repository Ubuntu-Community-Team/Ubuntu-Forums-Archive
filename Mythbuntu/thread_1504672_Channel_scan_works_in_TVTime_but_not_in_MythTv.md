---
title: "Channel scan works in TVTime but not in MythTv"
date: 2010-06-08
forum: Mythbuntu
---

### Post by dotbart on 2010-06-08
Hi all,

I'm trying to install a mythtv-backend for my home server.
I'm using a **Pinnacle Dazzle* Mobile**.

This device gets recognized as shown by lsusb:
```

bart@server:~$ lsusb
Bus 004 Device 002: ID 046d:c069 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2304:0208 Pinnacle Systems, Inc. [hex] Studio PCTV USB2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```When opening TVTime, and letting it scan for my region (Europe/Belgium). It find all the channels perfectly.

In Mythtv, I configured the card as a Analog V4L card.
Mythtv-setup recognizes it (it says Pinnacle PCTV USB2 [em28xx])

But channel scanning gives no results whatsoever.

I don't see entries in the logs (or I'm looking in the wrong place).


Any ideas?

Thanks,
Bart

---

### Post by LowSky on 2010-06-08
[http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick](http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick)

> Mythtv will not find any channels using its built-in scanner. Instead, you must create a channels.conf file using scan, a program included inside the dvb-utils package of most distros. Warning: the package may be called dvb-apps on some distros, and scan  may be called dvb-scan. Make a channels.conf like this: ```
scan /usr/share/dvb-apps/atsc/us-ATSC-center-frequencies-8VSB >  channels.conf
```and then import the channels.conf into mythtv using the channel scanner in mythtv-setup. It should find all your channels instantly.

In Fedora, the syntax for ATSC is: scan -a 0 -f 0 -d 0 -t 1 -A 1 /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB

Other than these problems, digital TV works flawlessly in mythtv. 

---

