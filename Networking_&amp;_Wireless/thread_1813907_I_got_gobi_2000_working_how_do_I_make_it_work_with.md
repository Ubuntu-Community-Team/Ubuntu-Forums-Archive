---
title: "I got gobi 2000 working how do I make it work with cgps"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by 7cardcha on 2011-07-28
It works like this.

cat /dev/ttyUSB0

Here is what is outputs$GPGSV,4,4,16,01,,,,32,,,,31,,,,29,,,*77
$GPGGA,175740.8,3544.068683,N,07852.407074,W,1,03,666.6,66.0,M,-50.0,M,,*50
$PQXFI,175740.8,3544.068683,N,07852.407074,W,66.0,196.87,513.82,3.35*41
$GPVTG,345.3,T,3933319975483646000000000.0,M,0.0,N,0.0,K,A*23
$GPRMC,175740.8,A,3544.068683,N,07852.407074,W,0.0,,280711,,,A*5A
$GPGSA,A,3,07,13,16,,,,,,,,,,666.6,666.6,666.6*30
$GPGSV,4,1,16,06,46,054,30,16,36,049,26,13,60,247,24,07,35,313,22*75
$GPGSV,4,2,16,23,45,198,22,03,61,063,20,08,09,305,,10,01,281,*77
etc etc

How do I make this work with cgps so I can get something out of it? Thank you very much.

---

