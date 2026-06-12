---
title: "Really distorted, glitchy sound in ZSNES"
date: 2009-11-12
forum: Multimedia Software
---

### Post by thedogisdead on 2009-11-12
Hi everyone,

Scratching my head with this one.  Sound is awful in ZSNES... all distorted and glitchy!

It's nothing to do with the internal mixer being up too high - other programmes are fine, including the GENS Megadrive/ Genesis emulator

It's really wierd -  sometimes some games will sound perfect when you start them up, and then turn awful after a few seconds.

Any help would be much appreciated!

Kind regards, 

Aaron

---

### Post by thedogisdead on 2009-11-12
Just tried using the OSS driver instead of ALSA... no luck

---

### Post by thedogisdead on 2009-11-12
Ah, I had a terminal running in the background that time and when I closed ZSNES, this is what it read:


'ALSA: underrun, at least 0ms.'

---

### Post by Yellow Pasque on 2009-11-12
Check your SDL settings and see what SDL package you have installed (i.e. -alsa or -pulse). Maybe try the libao driver instead of SDL.

---

### Post by thedogisdead on 2009-11-17
Hi... I've tried the following:

"  -ad <>  Select Audio Driver :
                  auto = Automatically select output
                  null = Null output
                   nas = NAS output
                   oss = OSS audio driver output 
                  alsa = Advanced Linux Sound Architecture (ALSA) output
                   esd = ESounD output
                 pulse = PulseAudio Output
                   sdl = Simple DirectMedia Layer output
"

How would I use the 'libao driver instead of SDL'?

Any ideas, anyone?  It's thoroughly ruining my enjoyment of ZSNES.

Thanks again!

---

### Post by sherl0k on 2009-11-17
I've always used -ad SDL and had smooth sound audio. Also, play with the frequency of the sound in ZSNES itself, that may help. I use 44100.

---

### Post by oakgrove on 2009-12-24
> **thedogisdead said:**
> Hi... I've tried the following:

"  -ad <>  Select Audio Driver :
                  auto = Automatically select output
                  null = Null output
                   nas = NAS output
                   oss = OSS audio driver output 
                  alsa = Advanced Linux Sound Architecture (ALSA) output
                   esd = ESounD output
                 pulse = PulseAudio Output
                   sdl = Simple DirectMedia Layer output
"

How would I use the 'libao driver instead of SDL'?

Any ideas, anyone?  It's thoroughly ruining my enjoyment of ZSNES.

Thanks again!

That's interesting that you've tried all of the different sound options and none of them helped.  I had the same issue you reported and when I changed the line libAoDriver="auto" to libAoDriver="oss". in the config file, it cleared it right up.  I tried all of the alternatives and it was the alsa option that was causing the random distortion.

---

