---
title: "Spdif on MSI RS480M2 (Realtek ALC658)"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by oled on 2006-06-03
Hello! I've just installed dapper 6.06 on my htpc.

There seems to be some minor dificulties, (won't shutdown after I installed ati gfx driver, but I can live with that)

What I can't live with is no sound! The htpc is connected to my surround reciever through spdif. I've run alsamixer and tried to unmute/turn up every options with no luck. 

Anybody got spdif working ? 

If I need to buy a new sound card what card should I buy to get spdif working. Need ac3 passthroug as well.

Anybody?

/OleD

---

### Post by oled on 2006-06-04
Nevermind. Messed arround with the mixer a bit more and got it working. Needed to switch to OSS in GUI sound mixer and enable digital-1. And in alsamixer iec958 had to be pcm, and iec958 playback = 0.

---

