---
title: "dapper and Jamlab"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by brujoand on 2006-10-01
hey,
i have a fresh install of dapper on a dell inspiron 5150.. And on my windows machine i had something called m-audio plug and play unit.. you plug your gitar into it, and it plugs into your USB, tadaaa.. u got sweet sounding gitar on ur pc.. now.. On linux i cant find any drivers.. there are mac drivers availeble but i dont know where to look for linux drivers exept with apt-cache.. Can anybody help plz?

this is the site for the plugandplay unit called jamlab
[http://www.m-audio.com/products/en_us/JamLab-main.html](http://www.m-audio.com/products/en_us/JamLab-main.html)


this is the site for the gitar software
[www.dsound1.com](www.dsound1.com)

thanx

---

### Post by Firefox79 on 2006-10-02
Hi,

in Linux, you usually don't have to download drivers for every piece of hardware - they are included in the kernel. Instead, you should check whether a device is supported in Linux BEFORE you buy the piece.
I don't have experience with the M-Audio JamLab, but since it's an USB device, you probably just have to plug it in and start using it :) It worked for me with the Edirol UA-25 USB Audio Interface.
You can check, whether the device is recognised with ```
aplay -l
``` Your device will be listed if it's ready.

Greetings

---

