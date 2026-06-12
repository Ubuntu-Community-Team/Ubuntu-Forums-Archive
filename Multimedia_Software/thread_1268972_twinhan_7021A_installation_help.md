---
title: "twinhan 7021A installation help"
date: 2009-09-17
forum: Multimedia Software
---

### Post by goksu on 2009-09-17
hello,

I have a twinhan 7021A USB that I am trying to get to work under 9.04.

lsusb reads

Bus 001 Device 007: ID 13d3:3207 IMC Networks DTV-DVB UDST7020BDA DVB-S Box(DVBS for MCE2005)

I have installed mythtv to my ubuntu desktop box hoping it would work with it. it did not.

through googling and reading around I found the below link.

[http://www.linuxtv.org/wiki/index.php/DVB-S_USB_Devices#TwinhanDTV_StarBox_II_-_DVB-S_.287021A.29](http://www.linuxtv.org/wiki/index.php/DVB-S_USB_Devices#TwinhanDTV_StarBox_II_-_DVB-S_.287021A.29)

it basically says that eventially it works and you need the following files
dvb-usb-vp702x.ko
dvb-usb.ko
and
dvb-usb-vp702x-01.fw
I even got the dvb-usb-vp702x-02.fw file.

obviously i need to install the files.
so what next?

do i have to copy these to the /lib/firmware/ directoy?

---

