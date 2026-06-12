---
title: "no sound please help"
date: 2009-09-02
forum: Multimedia Software
---

### Post by eraldo on 2009-09-02
I install ubuntu to dual boot with xp but i cannot get the dam sound to work, iv tried following tutorials but they don't appear to work, i have a realtek sound card and installed the realtek drivers and alsa and today install the alsamixer altho i thought i already had it but the alsamixer doesnt even run.

> eraldo@eraldo-laptop:~$ alsamixer
ALSA lib simple_none.c:1536:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument


My sound card appears to be reconized so i dont understand why i can hear nothing, no sound what so ever not when booting,youtube, or any format of music or video.

Please help this problem is driving me crazy and is taking up too much of my time, i probly would have switched to debian or something if i had another dvd/cd but i dont and i like the ubuntu interface and want to make it work.

Im on ubuntu 9.04

---

### Post by HappyFeet on 2009-09-02
Right click your speaker icon and select **open volume control**. Check volume settings and then click preferences to see what is checked off.

---

### Post by eraldo on 2009-09-02
Nothing appears to be checked, any more ideas?

---

### Post by eraldo on 2009-09-04
awesome help forum.......

---

### Post by ikisham on 2009-09-04
I read somewhere that you may have to add yourself to the *audio* group:
```
sudo adduser *username* audio
```

---

