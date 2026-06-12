---
title: "Open Source Radeon drives?"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Schmoove on 2006-08-08
I have a Radeon 9000 Mobility in my notebook and ATi decided to drop support for it in the latest drivers.
Therefore I always hear about these open source radeon drivers, but I can't find a website where I can download these?
Can anyone tell me how I can get my hands on these drivers and how I install them??

As far as I know there are three variants you can use in your xorg.conf file... correct me if I am wrong:

ati <-- standard
fglrx <-- ATi driver from their website
radeon <-- OSS driver

I am interested in the last one: "radeon"

---

### Post by Stinger on 2006-08-08
The radeon driver has AFAIK always been part of X.Org earlier known as XFree.
So you don't have to download or install anything , it has always worked out of the box for my old Radeon 7000 card.
Ofcourse the 3D hardware accelleration isn't quite the same , but it isn't bad either. :)
BTW the radeon driver supports 3D in cards up to Radeon 9200 , 9250 and 2D for the rest I would think.
Here are some links:

[http://dri.freedesktop.org/wiki/ATIRadeon]("http://dri.freedesktop.org/wiki/ATIRadeon#head-298bd23baafb9c2fad1774d1d2fa54bd2aa55e7d")
for the support.

[http://dri.freedesktop.org/wiki/DriTroubleshooting]("http://dri.freedesktop.org/wiki/DriTroubleshooting")
for troubleshooting.

There  seems to be a DRI configuration tool too ( I didn't know that ).
[http://dri.freedesktop.org/wiki/DriConf]("http://dri.freedesktop.org/wiki/DriConf")

---

### Post by whatever on 2006-08-08
"ati" and "radeon" belong together, if you put "ati" in your xorg.conf and have a radeon card, it will load the "radeon" driver.
both of them are included in the "xserver-xorg-driver-ati" package and should be installed by default. in fact this is the driver which will be automatically selected by the ubuntu installer if you got a radeon card (except x1k series).

if you f*cked up your xorg.conf you can execute 'sudo dpkg-reconfigure xserver-xorg' and select the "ati" driver.

---

