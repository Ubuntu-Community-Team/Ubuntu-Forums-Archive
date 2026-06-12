---
title: "Sounds pop and stutters in vlc"
date: 2011-08-05
forum: Multimedia Software
---

### Post by ilovesoad on 2011-08-05
Any time a new mp3 track plays in vlc, for the first few seconds, sound pops and stutters, and then the song plays normally. This happens each time a track ends, and a new one begins. I'm using 11.04 on an asus g50vt laptop.

---

### Post by Johnb0y on 2011-08-05
update VLC or check drivers for sounds card probably.... :confused:

---

### Post by ilovesoad on 2011-08-05
> **Johnb0y said:**
> update VLC or check drivers for sounds card probably.... :confused:
The vlc package I'm using i downloaded today, and I'm fairly certain my driver are ok, considering sound works fine elsewhere.

---

### Post by ilovesoad on 2011-08-07
bump

---

### Post by mc4man on 2011-08-07
You could try a couple of things - 
As shown here in post 18 - this could also help with pop and stutter
[http://ubuntuforums.org/showthread.php?t=1769271](http://ubuntuforums.org/showthread.php?t=1769271)

Based on one of the pulse fixes shown on fedora site - note that this is a global setting and could affect cpu
[http://fedoraunity.org/Members/fenris02/pulseaudio-fixes-and-workarounds](http://fedoraunity.org/Members/fenris02/pulseaudio-fixes-and-workarounds)

What I do with vlc is not use pulseaudio anymore, alsa instead. This takes care of any issues here

To try that you need to switch the ouput module to alsa AND pick the audio device. If you don't pick the device then you're still using pulseaudio thru the alsa plugin

The setting is in vlc > tools > preferences > audio  - screen 1
I use a built 1.2+ version of vlc where there are quite a number of choices for device ala audacious. In the 1.1.X you'll only see a few, pick most logical and ck. if you get sound. (click "save"

If so,  while vlc is playing if you open your sound preferences it should show no app using as in screen 2, then you know pulse isn't being used
(for the purpose of here used laptop that is on 11.10, same difference

---

### Post by ilovesoad on 2011-08-07
> **mc4man said:**
> You could try a couple of things - 
As shown here in post 18 - this could also help with pop and stutter
[http://ubuntuforums.org/showthread.php?t=1769271](http://ubuntuforums.org/showthread.php?t=1769271)

Based on one of the pulse fixes shown on fedora site - note that this is a global setting and could affect cpu
[http://fedoraunity.org/Members/fenris02/pulseaudio-fixes-and-workarounds](http://fedoraunity.org/Members/fenris02/pulseaudio-fixes-and-workarounds)

What I do with vlc is not use pulseaudio anymore, alsa instead. This takes care of any issues here

To try that you need to switch the ouput module to alsa AND pick the audio device. If you don't pick the device then you're still using pulseaudio thru the alsa plugin

The setting is in vlc > tools > preferences > audio  - screen 1
I use a built 1.2+ version of vlc where there are quite a number of choices for device ala audacious. In the 1.1.X you'll only see a few, pick most logical and ck. if you get sound. (click "save"

If so,  while vlc is playing if you open your sound preferences it should show no app using as in screen 2, then you know pulse isn't being used
(for the purpose of here used laptop that is on 11.10, same difference

Thanks! Added the audio device and this solved my issues.

---

