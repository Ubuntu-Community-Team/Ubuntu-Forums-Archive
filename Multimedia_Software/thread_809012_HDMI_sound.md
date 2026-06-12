---
title: "HDMI sound"
date: 2008-05-27
forum: Multimedia Software
---

### Post by anzevi on 2008-05-27
hello!

I have my LCD TV connected to my pc with HDMI cable. The problem is there is no sound from TV speakers.

OS: Ubuntu 6.06 LTS
kernel: 2.6.15-27-686
nvidia card: GeForce 6200
nvidia driver version: 169.12 (latest)
sound card: SoundBlaster Live!
alsa versions:
- alsa-base   1.0.10-4ubuntu4
- alsa-oss    1.0.10-1
- alsa-utils   1.0.10-1ubuntu14

Sound is working perfectly on the pc. 

My question is, does latest ALSA drivers supports sound over HDMI cable?

thank you

---

### Post by Trollslayer on 2008-06-01
> **anzevi said:**
> hello!

I have my LCD TV connected to my pc with HDMI cable. The problem is there is no sound from TV speakers.

OS: Ubuntu 6.06 LTS
kernel: 2.6.15-27-686
nvidia card: GeForce 6200
nvidia driver version: 169.12 (latest)
sound card: SoundBlaster Live!
alsa versions:
- alsa-base   1.0.10-4ubuntu4
- alsa-oss    1.0.10-1
- alsa-utils   1.0.10-1ubuntu14

Sound is working perfectly on the pc. 

My question is, does latest ALSA drivers supports sound over HDMI cable?

thank you

HDMI audio is still in it's early days (yes, I want it as well!:lolflag: ).
There are a lot of complications:
First, does your hardware support audio over HDMI?
Second, does ALSA - there is support for some systems from 1.0.14 onwards
Third - with HDMI audio there are two parts: the audio device and the routing. In my case the audio is a Realtek ALC883 and, as it's on the motherboard, the routing is part of that ATI SB600 south bridge.
Given all this, I managed to get it all working after setting the default sound output and unmuting it.
Next problem....
I bought a nice shiny AV receiver (Onkyo TX-SR606) and the audio stopped working. It seems ATI's HDMI audio implementation isn't very good because the audio device doesn't work under windows either.
All in all, early days and for the AV receiver I use HDMI video plus optical audio.
Hope this is of some help.

---

