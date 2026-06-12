---
title: "Which vdeo output driver for Intel graphics ?"
date: 2017-10-24
forum: Multimedia Software
---

### Post by linuxyogi on 2017-10-24
Hi,  I have installed an Asus h110 motherboard with Intel graphics. When I was using Nvidia graphics I used t select vdpau as video output driver.   Now that I am using Intel graphics which video output (in Smplayer) should I select ?

---

### Post by mc4man on 2017-10-24
You can use vaapi though depends on backend. mpv supports quite well, vlc is so-so, mplayer doesn't

---

### Post by linuxyogi on 2017-10-24
> **mc4man said:**
> You can use vaapi though depends on backend. mpv supports quite well, vlc is so-so, mplayer doesn't

When I select vaapi there is no video. Using mpv with Smplayer.

---

### Post by mc4man on 2017-10-24
> **linuxyogi said:**
> When I select vaapi there is no video. Using mpv with Smplayer.
What version of mpv? (mpv -v in terminal will show
Where are you setting this in smplayer? (- you should leave screen 1 as shown , set as seen in scr. 2

If need be attach smplyers mpv log, you have to set it to save to file, scr. 3 (if attaching either rename to .txt or compress to .gz

---

### Post by linuxyogi on 2017-10-24
> **mc4man said:**
> What version of mpv? (mpv -v in terminal will show
Where are you setting this in smplayer? (- you should leave screen 1 as shown , set as seen in scr. 2

If need be attach smplyers mpv log, you have to set it to save to file, scr. 3 (if attaching either rename to .txt or compress to .gz

I was setting it by going to preferences > General> Video > Output driver .

Now I have configured according to the attachments you have provided.

Videos are playing. Thanks a lot.

---

