---
title: "sound is very low in ubuntu as compared to windows"
date: 2008-09-09
forum: Multimedia Software
---

### Post by SheikhAmanAlam on 2008-09-09
Hello
recently, i have installed ubuntu 8.04.1,
and i have experienced that my sound output is very very low as compared to my windows system.
i use headfones, and have tried everythng from Sound applet to alsamixer in terminal.
every slider is set to the max level, still iam not getting the same sound output as i used to get in windows.
i have a dual boot system and my sound card is:Realtek High Definition Audio.
my mother board is : intel DG31PR.

after searching, i fond this howto-
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

is this what iam supposed to be doing to fix this??
please help

---

### Post by aeiah on 2008-09-09
are you using alsa or pulse-audio? in 8.04 i think pulse is the default so you might be going down the wrong track. that link goes about updating and installing alsa but if your system is set to use pulse this'll make no difference. i cant tell you how to change from pulse to alsa as im not on my ubuntu system, and i dont have 8.04 anyway im afriad

---

### Post by tuxxy on 2008-09-09
To select ALSA as your sound output navigate to system > prefs > sound and edit the top two optuions to ALSA, also play their test sound file first

---

### Post by SheikhAmanAlam on 2008-09-09
> **aeiah said:**
> are you using alsa or pulse-audio? in 8.04 i think pulse is the default so you might be going down the wrong track. that link goes about updating and installing alsa but if your system is set to use pulse this'll make no difference. i cant tell you how to change from pulse to alsa as im not on my ubuntu system, and i dont have 8.04 anyway im afriad

i am using alsa of course.
so increasing PCM and master in alsamixer did increase the sound, but a li'l bit only.
im amazed to see the difference between performance of windows and ubuntu.

---

