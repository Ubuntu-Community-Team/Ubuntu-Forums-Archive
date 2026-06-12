---
title: "MP3 problems.. guess its sound card"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by artofchobo on 2005-12-07
Hi guys,
I hope someone could sort the sound problem that i'm facing right now. I'm running ubuntu v5.04 on VMWare.
When I log on into ubuntu, the sound is alright
My gaim sounds works just fine but I cant seem to be able to play any mp3.
I have installed xmms and it freeze when i click play. Therefore, i got no choice but to kill it. The xmms was able to read the length of the song but it is not able to play it. I also tried using Totem but an error popped up "Totem couldn't start up    Resource busy or unavailable".

I checked the device manager and it seems like my audio driver is ES-1371 Audio PCI97 but in windows xp, its called "SigmaTel"

I hope there is enough info for you guys to troubleshoot.
Thanks
chobo

---

### Post by tomwell on 2005-12-07
chobo,

By default you can not play Mp3 in Ubuntu because Its is not free... you can however do searches on installing mp3 codecs....

Hope that helps...

Peace

Tom

---

### Post by VestniK on 2005-12-07
You need mpg123 it can be found on
[http://www.mpg123.de/](http://www.mpg123.de/)

---

### Post by artofchobo on 2005-12-07
Hi guys,

Problems solved after i have ctrl+P on xmms
In the eSoundOutputPlugins, choose Esound Plugins 1.2.10 [libesdout.so]
Before that you have to also check out
[https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary)
Read on the "general fix"
Thanks for all the assitance tomwell and VestniK...


Regards,
chobo

---

### Post by tomwell on 2005-12-07
Glad you sorted it out...

Peace

Tom

---

