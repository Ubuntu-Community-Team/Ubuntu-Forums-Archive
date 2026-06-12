---
title: "Problem with sound"
date: 2010-07-28
forum: Multimedia Software
---

### Post by fipem on 2010-07-28
Hi, I have an internal 7.1 sound card and a 7.1 surround system, since I can select 7.1 in sound option I have selected 5.1. Used to work fine until now, I've been trying to play a movie that have two audio tracks:

 audio tracks : 1. espanol AAC 2.0
.............. 2. ingles  AAC 5.1

The first one sound like any 2.0 channel but the second one, the 5.1, the voice sound on the rear left speaker. 

When I play this:

 speaker-test -Dplug:surround51 -c6 -l1 -twav 

at the terminal I got this:

speaker-test 1.0.22

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 349504
Period size range from 32 to 174752
Using max buffer size 349504
Periods = 4
was set period_size = 174752
was set buffer_size = 349504
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 22.109061

(the LFE sounds like the teacher from snoopy, I don't know if it's right to sound like that) :/

Of course the side speakers doens't sound since I can't select 7.1 on preferences... but that is not my main issue, the thing is that on this movie, when y play the 5.1 sound channel the voice sound come out in the rear left speaker (using XBMC, since it's the only app that play mkv without sttutering) instead of coming from the center speakers...

Any help how can I fix this? 

Thanks in advance...

---

