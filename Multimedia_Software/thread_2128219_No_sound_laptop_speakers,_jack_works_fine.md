---
title: "No sound laptop speakers, jack works fine"
date: 2013-03-22
forum: Multimedia Software
---

### Post by mafi127 on 2013-03-22
can some1 help me to get sound working in my laptop, sound works well when I plugin in headphones or speakers, but sound dont work in laptop speakers.
```
tamps@mafia ~ $ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant CX20561 (Hermosa)
```

```
tamps@mafia ~ $ cat /proc/asound/card0/pcm0c/info | grep name
name: CONEXANT Analog
subname: subdevice #0
```

I have followed this therd, but still audio dosent work.
[http://ubuntuforums.org/showthread.php?t=1741256](http://ubuntuforums.org/showthread.php?t=1741256)

Allso tryed to follow this tutorial [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but there dont have my sound card CX20561

My alsa information [http://www.alsa-project.org/db/?f=8c4d26af7c448519026d32e0d9bd4ab487640ab3](http://www.alsa-project.org/db/?f=8c4d26af7c448519026d32e0d9bd4ab487640ab3)

---

### Post by mafi127 on 2013-03-24
some1 ?

---

### Post by mafi127 on 2013-03-25
I have updated alsa using this script [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

I have edited /etc/modprobe.d/alsa-base.conf and checked all thows setups one by one, and then restart. options snd-hda-intel model=*
and checked every time after restart gnome-alsamixer that nothing isent muted. still no sound. 

```
Conexant 5051  Hermosa/CX20561
=============
  laptop    Basic Laptop config (default)
  hp        HP Spartan laptop
  hp-dv6736    HP dv6736
  hp-f700    HP Compaq Presario F700
  ideapad    Lenovo IdeaPad laptop
  lenovo-x200    Lenovo X200 laptop
  toshiba    Toshiba Satellite M30
```

Allso I have removed pulseaudio from system thought that this maybe was problem.

I have made a new alsa info script. [http://www.alsa-project.org/db/?f=a2681f6897142c43305688b6cd219e96feadecc9](http://www.alsa-project.org/db/?f=a2681f6897142c43305688b6cd219e96feadecc9)

can some1 plz help me to slove this problem, I'm out of ideas, I have searched google, but no success :(

-- EDIT -- 

Did fresh install sound still dont work, headphones works fine, allso the sound dident work from live cd. allso tried bios reset but no success

---

### Post by mafi127 on 2013-03-27
some! ? :S

---

### Post by mafi127 on 2013-04-01
hop :(

---

### Post by mafi127 on 2013-04-20
Problem still exist, havent found any solution yet :(

---

### Post by mafi127 on 2013-05-06
no help in this forum?

---

### Post by mafi127 on 2013-06-22
Upgraded to ubuntu 13.04 the problem still remains.

---

