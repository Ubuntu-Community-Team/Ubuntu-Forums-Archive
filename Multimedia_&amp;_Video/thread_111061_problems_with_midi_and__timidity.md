---
title: "problems with midi and  timidity"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by stratotak on 2006-01-01
having problems with midi..ive got midi up an working..but when i go into timidity.cong and chand source from  freepat to unison or any other sf2  file ive downloaded..have tried personel copy,fluid, and the sf2 off my audigy 2 cd..i get the same problem..timidity says "syntax error"..and gives up after a few tries...anyone else having problems with trying t get timidity to use anothe source other then freepats??it will work fine with freepats but wont work with any other sf2  i try..

---

### Post by FarEast on 2006-01-06
Hello stratotak,

To use a soundfont instead of freepats, you have to do the following:

1. Put the .sf2 file in /usr/share/midi .
2. Alter /etc/timidity/timidity.cfg as follows:
...
# source /etc/timidity/freepats.cfg <- comment out
dir /usr/share/midi
soundfont XXXXX.sf2 order=0

--
Regards,
FarEast

---

### Post by stratotak on 2006-01-06
thanks...that worked...

---

