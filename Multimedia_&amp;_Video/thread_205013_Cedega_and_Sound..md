---
title: "Cedega and Sound."
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by rivethead on 2006-06-27
Ive got Cedega running Ventrilo, it runs it fine after i figured it all out. Ive got it running the sound through Alsa, the problem im having though is while Vent is running nothing else can access sound. It says the device is busy, ive tried a number of guides located on this forum. Unfortunently none of them seem to work, can anyone tell me a good way in dapper to get multiple programs to be able to use alsa ? Id like to use vent and play quake4, but it doesnt seem to want to work for me.

Thanks!

-Rvt

---

### Post by dtfinch on 2006-06-27
I've had bad luck with ALSA in Dapper, with any program. When it works at all, it stutters. I've been using OSS in most programs, including wine.

Another thing I've had to do on occasion to make audio work in Flash is run "killall esd" to free up the audio device. I can't remember if I've had to do this since Dapper went final though.

---

### Post by rivethead on 2006-06-27
I have to run the vent through ALSA in cedega it's the only way it works , but i know i can run q4 with OSS , but is there a way to let oss use the soundcard too while vent is running on it with alsa? That ive tried many times too and cant seem to get it to work.

---

