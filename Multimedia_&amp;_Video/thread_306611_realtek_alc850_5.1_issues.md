---
title: "realtek alc850 5.1 issues"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by bunnythebunny on 2006-11-25
I've got a 5.1 surround system and my soundcard is an onboard Realtek ALC850.

only my front speakers and my subwoofer work. 

This is what happens when i test my speakers in 5.1

> bunny@bunny-desktop:~$ speaker-test -D surround51 -c6

speaker-test 1.0.11

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5461
Periods = 4
was set period_size = 5461
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Input/output error
Setting of swparams failed: Input/output error

but when i test them in surround40 -c4 they work just fine!  

how can i fix this?

---

### Post by jsteve54302 on 2006-12-01
> **bunnythebunny said:**
> I've got a 5.1 surround system and my soundcard is an onboard Realtek ALC850.

only my front speakers and my subwoofer work. 

This is what happens when i test my speakers in 5.1



but when i test them in surround40 -c4 they work just fine!  

how can i fix this?


Honestly?  If you can, get another audio card and disable the onboard...  I've seen at least 2 dozen posts asking how to fix this, and all of 2 fixes - and neither was satisfactory on my  system.  The best I could do with this (nVidia nForce4 CK804/ALC850) was get some sound from the rear speakers, and i had no volume control over that (and the few controls that did work, worked on a channel they weren't supposed to be on, i.e. slider for rear changed center/lfe (both)).  Fortunately, I had an Audigy ZS 2 from an old system, and it worked with no tweaking (other than enabling the proper channels in the Volume Control prefs ...)  And it's got better sound even than it did in xp (and even _that_ was better than the onboard)...

---

