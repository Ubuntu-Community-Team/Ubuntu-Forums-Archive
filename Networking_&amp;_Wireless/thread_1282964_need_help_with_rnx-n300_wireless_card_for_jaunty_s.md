---
title: "need help with rnx-n300 wireless card for jaunty server"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by bradw on 2009-10-05
greetings to all, 

here is what is going on. first of all i'm using a rnx-n300 card which is compatible with b and g networks. i'm running jaunty server so i have no gui. i'm trying to configure my wireless card via the terminal. i type in sudo ifconfig ra0 up and all goes well. no errors. then i type in iwlist ra0 scan and get this:

cell 01 - address: 00:21:63:6a:70:de
essid: "xxxxxxxxxxxxxxxxxx" (where xxxx...is my correct ssid)
mode: managed
channel:6
quality: 100/100 signal level:-50bdm noise level:-97dbm
encryption key:on
bit rates: 18 mb/s
ie: wpa version 1
group cipher: tkip
pairwise cipers (1): tkip
authentication suites (1) psk

then i run sudo iwconfig ra0 essid xx_xx_xx and no errors
then i run sudo iwconfig ra0 key s:xxxxxxxxxxxxxxxxxxxxxxxxx and get set failed on device ra0; invalid argument.

i also run various other iwconfig commands and get the same error whether i'm trying to set the channel, mode etc..

i'm new to linux and to jaunty *_**server**_* and just cannot figure out what i'm doing wrong. If you need more information, let me know what it is and maybe commands to get you the information and I can update. for now I have no clue what to do. 

thank you

brad:(

---

