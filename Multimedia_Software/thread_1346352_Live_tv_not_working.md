---
title: "Live tv not working"
date: 2009-12-05
forum: Multimedia Software
---

### Post by MMALLOW on 2009-12-05
HI
 
I USE UBUNTU 9.10
 
IM NOT ABLE TO WATCH LIVE TV
 
I INSTALED MMPLAYER , MOVE PLAYER, ALSO FIRE FOX BLUGIN
 
I DONT KNOW WHAT THE PROPLEM
 
FOR EX
 
[http://www.fomny.com/Video/Arabic-Radio/03/Goal-fm-radio/Goal-fm-radio.htm](http://www.fomny.com/Video/Arabic-Radio/03/Goal-fm-radio/Goal-fm-radio.htm)
 
[http://www.fomny.com/Video/Arabic-Radio/03/hezb-elshaab/hezb-elshaab.htm](http://www.fomny.com/Video/Arabic-Radio/03/hezb-elshaab/hezb-elshaab.htm)
 
[http://www.fomny.com/Video/Arabic-Radio/02/Amr-Diab/Amr-Diab.php](http://www.fomny.com/Video/Arabic-Radio/02/Amr-Diab/Amr-Diab.php)
 
[http://www.fomny.com/Video/Arabic/BBC-Tv/BBC-Tv.htm](http://www.fomny.com/Video/Arabic/BBC-Tv/BBC-Tv.htm)
 
FROM WHERE THE PROPLEM

---

### Post by MMALLOW on 2009-12-05
Can you give me the link for solving my proplem

---

### Post by xc3RnbFO8P on 2009-12-05
Here is codec for Karmic Koala:

> sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

> sudo apt-get install libdvdcss2

> sudo apt-get install w32codecs

> sudo apt-get install libdvdread4

> sudo /usr/share/doc/libdvdread4/install-css.sh

> sudo apt-get install ubuntu-restricted-extras

in Synaptic Package Manager install **gecko-mediaplayer**

---

### Post by MMALLOW on 2009-12-06
This codecs from terminal 
 
 
how i but it on terminal
 
if you have this codecs from synaptec 
 
its better to me beacuse i begener
 
NOTES in Synaptic Package Manager install **gecko-mediaplayer**
 
**ALLREDY I INSTALED THIS BUT UNTIL NOW NOT WORKING **

---

