---
title: "Genpix SkyWalker DVB card support"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by craig00 on 2008-04-04
I just did a fresh install of 7.10 and it seems that my Genpix SkyWalker DVB card is not recognized.  I know it works cause it runs under windows.  Are there some additional modules that I need to load?  

I thought this adapter was supported out of the box?

Thanks,

Craig
'

---

### Post by KetLock on 2008-04-07
I'm coming from windows myself and I was wondering how to set my genpix device on mythbuntu 7.10

---

### Post by svtcontour on 2008-04-07
> **KetLock said:**
> I'm coming from windows myself and I was wondering how to set my genpix device on mythbuntu 7.10

This is what I used :
> cd /usr/src/
sudo hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd /usr/src/v4l-dvb
sudo make
sudo make install 

What are you going to use with the Genpix?  There may be some patches that need to be applied to work properly.

---

### Post by xc3RnbFO8P on 2008-04-08
Its not supported  jet:
[http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices]("http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices")

---

