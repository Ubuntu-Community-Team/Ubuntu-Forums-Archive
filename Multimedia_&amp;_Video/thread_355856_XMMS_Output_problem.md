---
title: "XMMS Output problem"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by pattermj on 2007-02-07
Very new and attempting to convert my XP to an Edgy as I have no wish to use Vista. I used a Turtle Beach 7.1 audio card and use the optical output to my receiver for my music/movies. I have been able to get the optical and card working as when I go through preferences I can get it to do a test beep without a problem. When I try to change the XMMS output though I cant seem to get it to work at all. I have tried many different combinations of the audio possibilities and unless its on default PCM it says error not setup correctly. Any help would be greatly appreciated.

---

### Post by jpkotta on 2007-02-07
Try changing XMMS output to ESD.  You may need to install a plugin (just search for xmms in synaptic and look for esd or esound).  If you install a plugin, close xmms and restart it for it to find the new plugin.

---

### Post by pattermj on 2007-02-07
Ok thanks I will try it. I forgot to put in the title/message but I am also just trying to get all my system programs to run through my optical out. Is there anyway I can make everything just run through it as default or change it to my default? I went through my sound preferences and can do sound test through it without a problem.

thx

---

### Post by jpkotta on 2007-02-09
I'm pretty sure that the output test beep plays through ESD.  Pretty much all of the Gnome apps use ESD by default.  Most other apps will have an ESD option.  For anything that uses OSS (Flash is a good example), you can put a wrapper around it so that OSS gets redirected to ESD.
```
esddsp firefox
```
will make the flash plugin output redirect to ESD.  You may need to install esound-utils (or something like that) to get esddsp.  

Sound on Linux can be hard because there are many different ways to do it.  ALSA is the actual sound interface in the kernel.  ALSA has an OSS (legacy) emulation layer.  ESD, arts, and other sound servers can multiplex sounds into either ALSA or OSS.  ALSA can also multiplex sounds on it's own through dmix plugin, though OSS cannot do multiplexing (only one sound is played at a time).  Confused yet?  I am.

---

