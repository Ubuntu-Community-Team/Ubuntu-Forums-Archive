---
title: "no sound"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Isomorphismus on 2009-04-05
Hi everybody,
I know this topic is not new, but I really don't know what to do.
As the title says, my soundcard is not playing any sound, although it is detected by my ubuntu 8.04.

running aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then I run: head -n 1 /proc/asound/card0/codec*:
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices ID 194a

==> /proc/asound/card0/codec#1 <==
Codec: Generic 11c1 ID 1040

but trying to find this Codec in the file ALSA-Configuration.txt.gz , I fail ..
does anyone know how to get on? How to configure ALSA?

thx a lot,
Isomorphismus

---

### Post by bertolo on 2009-04-05
[http://ubuntuforums.org/showthread.php?t=1117215](http://ubuntuforums.org/showthread.php?t=1117215) look to my very first post.

---

### Post by Isomorphismus on 2009-04-06
Well, I looked at it, but my volume control looks somehow different than it should, I believe.When it opens, I just have on registercard called "Playback", where I can change the volume of "Master" and "PCM", and going to preferences, there I can just choose in the box "Select tracks to be visible" and then also "Master" and "PCM".
Where can I choose the headphones option an so on?

thx for help,
Isomorphismus

---

### Post by bertolo on 2009-04-06
in switch. my sound only get working until i selected headphone

---

### Post by Isomorphismus on 2009-04-07
and where is that switch?
I'm sorry, but I am an absolute beginner with linux..

---

### Post by Isomorphismus on 2009-04-07
Ok, via headphones the sound is working now.. 

greets, 
Iso:guitar:

---

