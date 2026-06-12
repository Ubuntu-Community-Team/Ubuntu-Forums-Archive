---
title: "[SOLVED] MythDVD Plays Only Homemade DVDs"
date: 2008-07-28
forum: Multimedia Software
---

### Post by kempy1000 on 2008-07-28
Hello,

MythDVD will play a homemade DVD perfectly fine. 
(Homemade DVD transcoded and copied by Nero Vision)

However if I put in a DVD purchased from a shop the screen flashes black and returns the mythDVD menu.

Thanks
Chris

---

### Post by samborambo on 2008-07-28
The package you need for decrypting commercial DVDs is called libdvdcss2 - a package not distributed with ubuntu for legal reasons (may not be legal in some countries).

There's a howto here for setting up the Medibuntu repository which includes libdvdcss2:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html")

Otherwise you can google for libdvdcss2.deb and install it with gdebi.

Hope that helps.

Sam.

---

### Post by kempy1000 on 2008-07-28
Worked Perfectly thanks!

---

