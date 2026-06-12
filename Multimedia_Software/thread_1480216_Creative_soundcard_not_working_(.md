---
title: "Creative soundcard not working :("
date: 2010-05-11
forum: Multimedia Software
---

### Post by netro_grant on 2010-05-11
Hey, I'm relatively new to linux and could use some help getting my soundcard to work on my linux box. I am running a soundblaster CA0106 soundcard under lucid and can't get it to produce any sound at all. 
The on board sound works fine when I select this as my output device however when I change the selected output device to the creative card it does nothing.

-----Things I have tried already---

I have checked all the volumes and mutes in the sound preferences AND alsamixer and there is nothing muted here.

I have re-named the ~/.pulse folder so as to force the computer back onto alsa (just re-named it ~/.xxxpulse)

I have tried all sorts of settings for the selected device and it is currently sitting on:

Digital Stereo ( IEC958 ) Output + Analog Stereo Input

none of this made any difference

help meeeee :(:(

---

### Post by netro_grant on 2010-05-14
No idea's anyone? :(

---

### Post by wlad0 on 2010-05-14
Hi,

pls, send here output of this commands:

```
aplay -l
```
```
lspci
```

or try this instructions
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

