---
title: "Pinnacle 73e usb can't scan"
date: 2010-12-25
forum: Multimedia Software
---

### Post by GoldWing on 2010-12-25
Hi,


Can somebody tell me what I forget ?
I have a Pinnacle 73e usb stick which works great under Windows Vista.
I don't seem to be able to scan under Kaffeine, it can't find any channels.

this is the part of dmesg (I think):

oliver@oliware-elite:~$ dmesg |grep dvb
[   14.673670] dvb-usb: found a 'Pinnacle PCTV 73e' in warm state.
[   14.673762] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.115956] dvb-usb: schedule remote query interval to 50 msecs.
[   15.115959] dvb-usb: Pinnacle PCTV 73e successfully initialized and connected.
[   15.116274] usbcore: registered new interface driver dvb_usb_dib0700


I think I installed the right firmware:


oliver@oliware-elite:/$ ls -l /lib/firmware/dvb-*
-rw-r--r-- 1 root root 12401 2010-05-26 18:10 /lib/firmware/dvb-fe-xc5000-1.6.114.fw
-rw-r--r-- 1 root root 34306 2007-09-10 11:09 /lib/firmware/dvb-usb-dib0700-1.10.fw
-rw-r--r-- 1 root root 33768 2010-05-26 18:10 /lib/firmware/dvb-usb-dib0700-1.20.fw
oliver@oliware-elite:/$ 


If I do a scan in Kaffeine, no channels are found, although the stick is recognized.

OS= ubuntu 10.04 all new updates

---

### Post by GoldWing on 2010-12-26
I did everything from here, but still no luck.

[http://www.smovs.dk/linux/index.php?note=17&subject=Pinnacle%20DVB-T%20nano%20stick%20%28PCTV%2073e%29](http://www.smovs.dk/linux/index.php?note=17&subject=Pinnacle%20DVB-T%20nano%20stick%20%28PCTV%2073e%29)

---

### Post by xc3RnbFO8P on 2010-12-26
Did you read this:
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_nano_Stick_(73e)]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_nano_Stick_(73e)")

---

