---
title: "[SOLVED] music not playing"
date: 2008-07-24
forum: Multimedia Software
---

### Post by wiseguyxp on 2008-07-24
I have Ubuntu 8.04 installed and have been recently trying to get music files to play on my laptop.  I can watch and hear videos on youtube fine, but local sound files don't play.  I can also hear the sounds from my virtual Windows XP machine inside of virtualbox-ose, but I haven't tested music files on it.

---

### Post by flamethrower on 2008-07-24
well?

what kind of files were u trying to play?
what software did you use to play these files?
have you tried different players?
can u pipe junk into /dev/dsp and hear it?

dont you think it would be a bit helpful to elaborate on your problem instead of simply sobbing "doesnt work"?

---

### Post by wiseguyxp on 2008-07-24
I guess you don't call yourself flamethrower for nothing, eh?

I don't know too much about the sound system of linux, so I didn't know exactly what details to include.  I would like to use Exaile, but I have tried Totem and Rhythmbox also.  I am trying to play mp3 and wav files.  Video files (avi) will play, but they don't output any audio.  I just realized from what I was about to say that it appears that using VirtualBox actually steals the sound device for whatever OS it is running, and doesn't play nice and share.  Ergo, I won't have sound on my linux machine while running Windows XP in my virtual machine, so I obviously tried youtube while my virtual machine wasn't running.  Thanks, flame, and I would hardly call that sobbing.

---

