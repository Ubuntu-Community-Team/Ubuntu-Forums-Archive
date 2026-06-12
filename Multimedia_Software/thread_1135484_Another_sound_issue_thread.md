---
title: "Another sound issue thread"
date: 2009-04-24
forum: Multimedia Software
---

### Post by markitoxs on 2009-04-24
Hello everyone,

I have been following the threads yesterday and today to try to find a solution for my problem but unluckily no success yet. 

I upgraded from 8.10 to Jaunty. The issue is basically that i only get sound from the headphone jack, but as opposed to suggested in the forum, the issue does not seem to come from having the front speakers muted or at a low level. 

If I go to alsamixer, PCM, seems to be active, but unable to be muted. I explain: usually underneath the bar, you get a square with two zeros on a green background that switch to two M' s when muted. See the screenshots attached. On gnome-alsamixer, the button for mute the PCM channel is gone as well. Using the PulseAudio applet, I make sure that the playback, and the output devices volume are up. If I use the Volume Meter for playback under the pulseaudio applet, while playing music, I can see that the sound is being played, but extremely low. 

I have tried adding to alsabase.conf the line 
```
options snd-hda-intel model=hp
```

Obviously without any success. Any ideas?

```

[B]lspci | grep Audio
[/B]
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

[B]aplay -l
[/B]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by markitoxs on 2009-04-24
Moved to: [http://ubuntuforums.org/showthread.php?t=1134447](http://ubuntuforums.org/showthread.php?t=1134447)

---

