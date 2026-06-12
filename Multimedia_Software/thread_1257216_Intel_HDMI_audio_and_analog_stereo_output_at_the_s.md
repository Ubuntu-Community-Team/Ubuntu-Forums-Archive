---
title: "Intel HDMI audio and analog stereo output at the same time"
date: 2009-09-03
forum: Multimedia Software
---

### Post by wouzs on 2009-09-03
I have a Asus p5q-em motherboard running Ubuntu 9.04 on it. I wanted to use the HDMI audio output so I installed the most recent version of Pulseaudio (0.9.15). Since this new version the HDMI output was properly detected. When I watch a movie I manually set the audio output to HDMI using the pulseaudio mixer (configuration tab).

When I change the output all sound goes to my TV. Is there a way to make the movie sound come out of the TV, and play some music on the analog stereo output at the same time?

Here is some information about my config:
```
gebruiker@pc-huiskamer:~$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: Intel [HDA Intel], apparaat 0: ALC1200 Analog [ALC1200 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 1: ALC1200 Digital [ALC1200 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 3: INTEL HDMI [INTEL HDMI]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
``````
gebruiker@pc-huiskamer:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```

---

