---
title: "Missing the surround setting from alsa"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by onion221 on 2007-12-13
```
speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 12 to 5461
Period size range from 6 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
0 - Front Left
4 - Center
1 - Front Right
3 - Rear Right
2 - Rear Left
5 - LFE
Time per period = 8.530563
```

There is no surround in volume control no left, right,rear l, rear r option either aren't there supposed to be? I run the speaker test and i hear front center, and then it comes around and tells me rear center which I thought was odd.

I have a Diamond XtremeSound 7.1/24 bit Sound Card

here is a screen of my alsa

I just want the front center to work  :sad:

---

### Post by d0nny2600 on 2007-12-13
Try this:

Open a terminal and type
gksudo gedit .asoundrc

Enter the following data 
pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

See if that allows you to hear all your speakers

---

### Post by onion221 on 2007-12-13
I put that in the asound nothing happened do I do anyrthing after that?

---

