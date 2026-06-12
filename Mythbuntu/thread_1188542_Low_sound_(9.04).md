---
title: "Low sound (9.04)"
date: 2009-06-15
forum: Mythbuntu
---

### Post by jboss1995 on 2009-06-15
I have an Intel DG965MQ motherboard (BIOS Current). The sound works nice on mp3 using VLC Media Player but when I play a DVD on XINE or watch tv on mythtv sound is vary low. I have looked at the mixer and made sure that all are turned up. Any thoughts?

Justin

---

### Post by bcg30506 on 2009-06-16
I had a similar issue and was able to fix it by running alsamixer -V playback from a terminal.  There I noticed the Front level was at zero. I raised it to 100 and voila, normal sound!  ymmv

---

### Post by jboss1995 on 2009-06-21
No Help, thanks though.

---

### Post by azmyth on 2009-06-21
In your frontend under setup -> general I'd check the initial settings for mixer control, master mix, and PCM mix.

---

### Post by spoolboyy on 2009-06-28
After a fresh install of Mythbuntu 9.04, I had the same problem but only after installing the updates.

I went to 'Aumix' under Applications -> Multimedia -> Aumix

and set it from 0 to 100.  That was my issue.  I hope it helps.

-Adam

---

