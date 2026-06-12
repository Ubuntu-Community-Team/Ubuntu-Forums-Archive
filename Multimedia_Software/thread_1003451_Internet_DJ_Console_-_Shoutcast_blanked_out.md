---
title: "Internet DJ Console - Shoutcast blanked out"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Naiki Muliaina on 2008-12-06
I downloaded IDJC from the Ubuntu repos on Ubuntu 8.10 64bit. When I go to Server -> Type , Shoutcast appears to be un-selectable. Is there something else I need to download to select this? 

Thanks for any replys :)

---

### Post by depert on 2009-01-27
well, i had the same problem days ago. but after i update my lame and libmp3lame using files from here. 
[http://debian-multimedia.org/pool/main/l/lame/lame.php](http://debian-multimedia.org/pool/main/l/lame/lame.php)
 and also you have to compile idjc from source.

Add option --enable-lame when configure :

after extract tar.gz file,

./configure --enable-lame
make 
sudo make install

now, shoutcast active. i hope it works to you too.

---

### Post by Delta6 on 2009-11-18
hi there, please bare with me at the mo cuz im a proper linux noob and this is the 1st time iv posted on here! lol.

right here i go..... iv got the same problem as above but i dont have a clue what i have to do to solve the problem, any chance someone could explain in SUPER noob lingo??? ;)

Many thanks ppl!

---

