---
title: "Help with iMon LCD please"
date: 2015-05-21
forum: Mythbuntu
---

### Post by Callandor64 on 2015-05-21
Hi everyone,

I have been running Mythbuntu 12.04 for a couple of years now. When I installed it (clean install from ISO) it automatically picked up that I have an iMon LCD display (this one is the OEM model in the Antec Remote Fusion Black case: [https://www.mythtv.org/wiki/File:Imon_lcd.png](https://www.mythtv.org/wiki/File:Imon_lcd.png)). I didn't have to enable anything, and it worked immediately with all the extra icons etc fully functional and used by mythtv.

Fast forwards to about an hour ago and I just tried a clean install of Mythbuntu 14.04.2 and the LCD drivers are not installed. I have got basic support for it by

```
apt-get install lcdproc
```

and editing /etc/LCDd.conf to specify driver = imonlcd

This is the only edit I have made to the files and this gets me the basic 16x2 line display level working, but none of the other awesome features from before. Any ideas how to get this back? All ideas are much appreciated! I still have the 12.04.3 install ISO if this is useful.

Cheers,

Mark

---

### Post by Callandor64 on 2015-05-23
Solved:

1) LCDd.conf the change /dev/lcd0 to /dev/lcd2 was required. No lcd0 or lcd1 entries were present in /dev. I found it hard to locate this information elsewhere.
2) driver = imonlcd
3) In the imonlcd settings towards the bottom of LCDd.conf I needed protocol 1 (My display has usb identifier 15c2:0038). The same subsection also lets you tell the lcd to display a clock when there is no client connected. Alas you cannot change the slightly hard to read font for this!

Cheers,

Mark

After this

---

