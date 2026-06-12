---
title: "Mysterious Dissappearing Sound"
date: 2010-03-04
forum: Multimedia Software
---

### Post by khaarvan on 2010-03-04
I'm having some trouble with sound - specifically my lack of it.  I'm running 9.10 Netbook Edition on a Toshiba nb 205.  I've been playing around with the sound/mic for quite a while, with limited success.  During my latest effort to get audio to work in skype, however, I must have mangled something, because I no longer have any sound.  After purge and reinstalling everything audio I could think of, I am still without sound.

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
shows
                              USER        PID ACCESS COMMAND
/dev/snd/controlC0:  c      1483 F.... pulseaudio
/dev/snd/pcmC0D0c:   c      1483 F...m pulseaudio
/dev/snd/pcmC0D0p:   c      1483 F...m pulseaudio

and 
grep 'audio' /etc/group
shows
audio:x:29:pulse,timidity,c

I've been checking alsamixer and such, but I've had no luck (although the settings change by themselves, it seems)

Does anyone have any ideas?

---

### Post by mörgæs on 2010-03-05
Have you made so many changes that a clean install is getting necessary? 

There are some good threads here:
[http://ubuntuforums.org/showthread.php?t=1203480](http://ubuntuforums.org/showthread.php?t=1203480)

---

