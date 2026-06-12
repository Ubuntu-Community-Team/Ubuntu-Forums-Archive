---
title: "External Mic recording only in Mono for Audacity"
date: 2009-07-28
forum: Multimedia Software
---

### Post by spraveenitpro on 2009-07-28
Hi 

My external mic is recording only in Mono in Audacity even though I have selected  Audacity > Edit > Preferences > Recording > Channels > Stereo , 
I am using Jaunty 9.04 , thx

Praveen

---

### Post by igorzwx on 2009-07-28
Audacity is very problematic with PulseAudio.
But it works well with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

try to record with "arecord"

on terminal:

man arecord

this would print to Terminal a manual

arecord means ALSA record

---

### Post by spraveenitpro on 2009-07-28
Hi 

thx for that, any thoughts on fixing this so that I can do stereo recording in Audacity , thx again, 

Praveen

---

### Post by igorzwx on 2009-07-28
try change everything to pulse 
in system settings, in Audacity settings, etc.

---

### Post by igorzwx on 2009-07-28
if it does not work -> Audacity forum

---

