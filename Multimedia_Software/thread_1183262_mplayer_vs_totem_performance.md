---
title: "mplayer vs totem performance"
date: 2009-06-09
forum: Multimedia Software
---

### Post by skibrianski on 2009-06-09
This is more of a curiosity than anything else, but I routinely find that mplayer is much faster than totem, especially with high definition videos. mplayer drops fewer frames and doesn't have to crank my laptop's cpu all the way up to full blast while it's doing it. Which means if I want to watch a couple of videos, and one is high def, I can't just queue them up in totem, but instead have to launch them one after the other in full screened mplayer with a little shell script.

Has anyone else experienced this, and if so, any ideas on what the technical reasons for this might be?

I've got a core2duo, 2.33GHz, and an nvidia Quadro NVS 110M/GeForce Go 7300, using the nonfree nvidia driver.

Thanks for any ideas...

---

### Post by logos34 on 2009-06-09
yeah, cpu overheard for HD video playback on mine (x64 8.04) is easily 15-20% higher for totem than for mplayer, but for regular dvd playback totem is the lowest

---

### Post by Arup on 2009-06-10
Enable vdpau with your mplayer in case you are using nvidia card and the performance is even stellar with way less CPU use even with HD movies played full screen.

---

