---
title: "No sound control in tvtime!"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by mirceatl on 2006-11-27
I can't change the sound volume in tvtime with the left
or right arrow from the keyboard. If I try this, the
OSD shows me that I can change the volume only between
99% and 100%. This is a real problem when I try to
use my remote (with lirc).

 I have tvtime 1.0.1-2 on an ubuntu Edgy with Creative
Audigy 4 sound card.

 I can change the volume of the sound only from one of 
the system mixers (kmix or alsamixer).
 Please help me, thank you.
mirceatl

---

### Post by mirceatl on 2006-11-28
help! ](*,) 
mirceatl

---

### Post by mirceatl on 2006-11-29
:( 
mirceatl

---

### Post by mirceatl on 2006-12-09
Interesting!
I have almost the same problem with Xmms. If I try to use the volume button on Xmms, nothing happens! If I try to use the UP or DOWN arrows from the keyboard the display on Xmms shows me that the Volume is changing only between 0% - 1% and the volume button jump in the left side of his place!
No ideeas?
Sorry for my english!
mirceatl:???:

---

### Post by Caraibes on 2006-12-10
Same problem : I can change the volume in TVTime with alsa mixer, but not directly inside TVTime. I do have the same problem in XMMS.

My other problem is that Real Player doesn't have sound. Nor Audacity... I don't know what happened :

This is an Edgy fresh install, with the ATI drivers, and most Automatix stuff...

The soundcard is a C-Media PCI CMI8738.

I am wondering what caused that problem.

---

### Post by mirceatl on 2006-12-11
OK! Worked for Xmms: -> options ->preferences ->audio io-plugins->output plugin->configure-> Mixer device list -> Master for ALSA plugin!.
  But no success with TVTIME! I lauched tvtime from terminal with the option --mixer=DEVICE where DEVICE were all the options I find in >man tvtime and all I get was:
mixer:Can't open device DEVICE , mixer volume and mute unavailable.
If I look with google for " mixer volume and mute unavaible" I can find some topics but none is enough clear! It seems to be a problem of root access?!?
I amm still looking for this
mirceatl
Multumesc,

---

### Post by lazerradial2003 on 2006-12-13
I'm having a similar problem, the system volume control does nothing but i can individually change the volume of the different channels. I don't know if this could be something to do with surround sound?

---

### Post by cblanquer on 2007-01-14
Same problem to me for a fresh reinstall.
Totem sound cannot be heard, using arrows the volume bar appears and remains ZERO.

The curious stuff is that 1 month ago the same reinstall worked well..? Only change to my former H/W is a webcam. Or any changes in available codecs since 2007.
Any solution ?


(For the little story: I also have trouble playing mp3 format from Totem, codecs are not found but other apps can play them) :-k

---

