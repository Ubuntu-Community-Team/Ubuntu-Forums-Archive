---
title: "Nvidia driver installed, monitor sync no go"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by bnortham on 2006-06-16
So I have read every thread here about installing and configuring Nvidia drivers for my GeForce 4 MX 440 AGP 8X.  The installation worked perfectly, driver is installed.  Enabling the driver, however in xorg.conf and restarting X causes by monitor to be out of sync range.  Monitor is a ViewSonic VX2000 and the Monitor (including HorizSync and VertRefresh) and Display subsections of xorg.conf work perfectly if Driver is listed as "nv".  Switching it to "nvidia" and restarting X causes the out of range problem, without changing any other value in the conf file.  Any ideas?

Brent Northam
Kubuntu 6.06

---

### Post by wahman143 on 2006-06-16
Hi Brent,
I had a similar issue with the EXACT same card on a Gentoo installation a while back...I had to add the following to my /etc/X11/xorg.conf file, under the "Device" section:

```

Section "Device"
     Identifier  "Geforce 4 MX400"
     Driver  "nv"
     Option  "IgnoreEDID" "true"
EndSection

```

The explaination I got from a very helpful person on that forum was that my monitor (A TTX 19" CRT) was causing some sort of issue with the nv driver, and by adding that IgnoreEDID line, it enabled me to iron out the conflict.  

If that does not work for you, post up your /etc/X11/xorg.conf and /var/log/Xorg.0.log files and I'll take a gander at them.

Cheers,
W.

---

