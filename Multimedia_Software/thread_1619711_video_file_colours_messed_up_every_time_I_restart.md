---
title: "video file colours messed up every time I restart"
date: 2010-11-12
forum: Multimedia Software
---

### Post by pickarooney on 2010-11-12
I have this annoying little problem in Lucid - every time I reboot and play a video file the colours are messed up. I need to manually increase then decrease the hue or saturation to get the picture to normal in smplayer. The colours aren't competely inversed as in the common bug with the totem sliders, they're just far too red and bright.

Smplayer is the latest from PPA. I've checked the totem settings and everything is OK. It only takes two key presses to resolve but it's a pain, to be honest, so if anyone knows what causes this and how to fix it permanently I'd be much obliged.

---

### Post by ajgreeny on 2010-11-12
Totem and smplsyer are totally different applications and use different backends, so changes in totem will make no difference to smplayer.

The backend for smplayer is mplayer, not totem, so try making changes to the video settings in mplayer ands see if that sticks.  I don't use smplayer but I do use mplayer so can not help any more than that for smplayer, I'm afraid.

---

### Post by pickarooney on 2010-11-12
> **ajgreeny said:**
> Totem and smplsyer are totally different applications and use different backends, so changes in totem will make no difference to smplayer.

They shouldn't, but historically they have - totem's hue bug affected lots of other players. I'll try looking at mplayer's conf file and see is there anything about default picture settings but the problem is really that the picture on startup doesn't match the settings that are there.

---

### Post by pickarooney on 2010-11-12
There's a really annoying glitch where once in every video file the pictrue will jump forward a second too, but I think that's unrelated.

---

### Post by pickarooney on 2010-11-16
Has nobody else experienced this?

---

### Post by no2498 on 2010-11-16
play a vid in totem then reset to default after it looks good
is what helped me anyway 
i use smplayer if totem dont play a video

---

### Post by pickarooney on 2010-11-22
I've tried that but it's still messed up after each reboot - in vlc, xine, totem, smplayer... Really weird.

---

### Post by pickarooney on 2010-12-11
I reformatted and installed Maverick today and this is *still* happening.

---

### Post by scan.tron on 2010-12-12
i have the same problem in vlc but i get too much yellow

---

### Post by pickarooney on 2010-12-12
Have a look at your nvidia driver settings (if you have an nvidia card) and see is the Hue or any other sliders off-centre. I noticed this in mine yesterday and set it back to 0. The first video I tried today looked better, but I'm not sure someone else didn't already fix the settings after loading a video.

---

