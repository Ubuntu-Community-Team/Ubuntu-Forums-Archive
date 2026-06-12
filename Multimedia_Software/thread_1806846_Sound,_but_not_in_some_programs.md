---
title: "Sound, but not in some programs"
date: 2011-07-18
forum: Multimedia Software
---

### Post by mtguy on 2011-07-18
I had a problem with sound, but after googling and installing a couple of files, I finally got sound from youtube and in aqualung.  However, still nothing from audacious or amarok.  When I open them with a terminal, there are no error messages.  In audacious, the visuals show that the song is playing...the volume is at 100%, but no sound.  Same with amarok.  Any help?

---

### Post by Johnny Buffalkill on 2011-07-20
This is just a guess, but it might be that the different programs are set to use different sound drivers.  I've played around with Kubuntu a little, and I always found that anything using ALSA as the sound driver was silent by default.  Try entering 'alsamixer' into a terminal, and see if the master volume is turned all the way down.

---

