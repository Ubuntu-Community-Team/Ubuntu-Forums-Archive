---
title: "HDMI audio 2 channel only?"
date: 2009-01-24
forum: Multimedia Software
---

### Post by korgman on 2009-01-24
I installed Alsa 1.0.19 today in hopes of getting HDMI audio working.  Upon installation and reboot I got the first piece of good news:

```
matt@mythbuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And then:
```
aplay -Dplughw:0,3 -fcd falcon_flyby.wav

```produced audio.  Success!

```
matt@mythbuntu:~$ speaker-test -Dplughw:0,3 -c6

``` produced pink noise only in the left and right though it tried all 6 channels.  So, its a good start.  I just started learning about alsa today, so I guess I should add that I do **not** have a ~/.asoundrc or /etc/asound.conf on the system.  Definitely would like to get the surround sound working with this.  Anyone have any ideas?

Matt

---

### Post by korgman on 2009-01-25
Well, I found a /etc/asound.conf example online and put it in. Now I'm getting 6 channel sound in Myth, but I'm still not getting more than L/R when I run the speaker-test or aplay from the cmd line. I haven't tried playing anything from Myth in hours. Who knows how long ago it got fixed.

I did update the nvidia driver to 180.22, so maybe right around then. Myth was defintely 2 channel earlier today.

---

