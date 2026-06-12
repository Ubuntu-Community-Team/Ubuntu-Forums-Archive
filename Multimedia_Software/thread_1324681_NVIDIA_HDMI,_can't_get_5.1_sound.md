---
title: "NVIDIA HDMI, can't get 5.1 sound"
date: 2009-11-12
forum: Multimedia Software
---

### Post by sherl0k on 2009-11-12
```
sherl0k@evergreen:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
sherl0k@evergreen:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

If I do "speaker-test -Dhdmi -c2" I get left and right speakers. If I do "speaker-test -Dhdmi -c6" I get nothing at all.

Using the 190.42 NVidia drivers, and kernel 2.6.31-15.

Anyone got any ideas?

---

### Post by Lucky75 on 2009-11-12
See my thread, just got it working.

[http://ubuntuforums.org/showthread.php?t=1320013](http://ubuntuforums.org/showthread.php?t=1320013)

Essentially, I had to specify model=3stack, and use the RC6 kernel.

---

### Post by sherl0k on 2009-11-12
Wish it were that easy for me. :| I have to recompile ALSA everytime, using the [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1046137") and fixing up patch_nvhdmi.c to add my card. And the script doesn't work with 2.6.32. So using this kernel, I don't even get HDMI output in my aplay -l. Really dumb stuff.

Guess I'll have to wait for everything to stabilize itself. I mailed one of the ALSA devs my patch, hopefully he'll add it in before the next revision. And I'll be able to upgrade to it with the new kernel.

Thanks for the assistance though, I'll definitely be using this info once when everything else falls into place. :)

---

### Post by sherl0k on 2009-11-13
Alright, I compiled ALSA by hand with my patch and I'm back to where I started with 2.6.32-rc7. speaker-test still isn't giving me surround sound via HDMI. Now I'm really at a loss, I was hoping this would work :<

---

