---
title: "DVB on ATI but slow graphics"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by irober02 on 2006-11-27
I'm running Dapper (kernel 2.6.15-27-686) on a Dell Inspiron 6400 with an ATI Mobility Radeon 1400 graphics adapter (v8.28.08 driver downloaded from ATI). I've purchased a tinyUSB2 DVD-T and after installing the firmware it initialises correctly (dmesg: dvb-usb: Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II).

kaffeine can control the device and I've scanned the local stations and have a strong and clean signal.

The TV is unwatchable.:( 

The sound is fine but the video is very slow.

I can't find any obviously relevant error messages and am not sure whether I have an X server config problem, ATI driver problem, dvb-usb device problem, kaffeine problem or something else.

My xorg.conf file is as the ATI installer left it and in other respects seems to be OK. I've tried a couple attempts at disabling composite mode (whatever that is) after reading some postings that sounded like my problem, with no apparent change. 

Any suggestions?

BTW The aforementioned equipment all works pretty well when I boot into (shock, horror) Windows.

---

### Post by sjhupp on 2006-12-06
Hi, in case you hadn't solved this, I had a similar problem with ATI graphics. Apparently I had "MESA" drivers instead of proper ATI ones (even after installing all the ATI stuff). Search for enabling Xv for ATI and you should be ok. once changed mine looks magnificent.
Good luck.

---

### Post by irober02 on 2007-01-11
I tried quite a few things (all using the correct ATI/fglrx drivers) without success UNTIL I upgraded to Edgy and all was good. It seemed to be impossible to get direct rendering working in Dapper -impossible for me at least.

---

