---
title: "Laptop Speakers not working on HP Pavilion dv3000"
date: 2009-06-08
forum: Multimedia Software
---

### Post by jackvaughn on 2009-06-08
I'm pretty new to using Linux and recently did a clean install of Ubuntu 9.04 on a HP Pavilion dv3000.

Everything seems to be OK, except that sound is only playing through the the headphones (weirdly, only through headphones socket 1 and not 2)

When the headphones jack is removed, sound will not play through the laptop speakers.

I've read through other threads where the problem seems to have been resolved, i've edited etc/modprobe.d/alsa-base.conf and added the line 
options snd-hda-intel model=hp-m4 enable_msi=1
at the end, and have tried various other lines suggested too.

I've also upgraded to ALSA 1.0.20

However, nothing I have tried has worked. 

Any ideas?

---

### Post by jackvaughn on 2009-06-08
Typical. You post a thread and suddenly it all starts working!

Although oddly, headphone jack 2 still doesn't work, although I think I can live without it for now!

---

### Post by isparkes on 2009-10-27
Confirm that this solved the problem for me as well on Karmic.

edit etc/modprobe.d/alsa-base.conf and add the line:
options snd-hda-intel model=hp-m4 enable_msi=1

No need to do anything else.

---

### Post by rmvasuki on 2010-06-14
> **isparkes said:**
> Confirm that this solved the problem for me as well on Karmic.

edit etc/modprobe.d/alsa-base.conf and add the line:
options snd-hda-intel model=hp-m4 enable_msi=1

No need to do anything else.

I had the same problem on a Compaq CQ-61 Notebook. 
Did what you said and it works just fine now!
Thanks!):P

---

