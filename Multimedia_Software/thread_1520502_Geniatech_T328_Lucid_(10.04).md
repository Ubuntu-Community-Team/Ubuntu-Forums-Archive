---
title: "Geniatech T328 Lucid (10.04)"
date: 2010-06-29
forum: Multimedia Software
---

### Post by XenonTW on 2010-06-29
Hi, 

I have an Geniatech T328 DVB-T stick and it worked fine under Karmic. I didn't have to install any driver I just plugged it in and it worked fine. Since I have Lucid I doesn't: When I plug it in an error message comes up that no driver is available under /lib/firmware/
(I know that under Karmic there was no driver needed the /lib/firmware/ was empty)

So I downloaded the driver from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw)

and put in in /lib/firmware everything seems fine lsusb and dmesg shows me the stick as usual. But when I do a scan for channels it says "tuning failed". I tried scan and w_scan as well. The antenna is at the exact same place where I had good signal under Karmic. 

I don't understand it ...

---

