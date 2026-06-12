---
title: "Audio setup questions (pulseAudio vs card for output device)"
date: 2009-09-30
forum: Multimedia Software
---

### Post by kbm on 2009-09-30
I recently set up my new Dell studio 15 laptop with Kubuntu 9.04.  I had to add "options snd-hda-intel=dell-m6" to the end of modprobe.conf and alsa-base.conf to get sound working, but it seems to be working fine with two exceptions:
[LIST]
[*]I kept getting notifications that HDA Intel (STAC92xx) wasn't working, failing over to PulseAudio
[*]Dragon player had no sound.
[/LIST]
I fixed both it seems by going into System Settings -> Multimedia and setting PulseAudio as the highest priority for all the output types.  Only problem is that I really don't understand what I just did.  My soundcard is from the intel ICH9 family, which ALSA does not claim to have a driver for, but my sound is working.  So (a) what is going on here and (b) what are the implications of the change that I made?  I figured that I had ALSA working, but now I'm not so sure.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v
<clip>
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02be                                                      
        Flags: bus master, fast devsel, latency 0, IRQ 22                                
        Memory at fc700000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel 
<clip>
```

---

### Post by markbuntu on 2009-10-01
The ICH9/STAC92xx has had an alsa driver for quite a while now. Alsa drivers are part of the kernel.

Kubuntu uses the phonon sound server but if you have pulseaudio installed phonon will not be able to gain control over the hardware if pulseaudio has already grabbed it. That is why you got those messages. When you told phonon to use pulseaudio instead of the hardware driver directly you resolved this conflict.

I hope that explained it for you.

---

### Post by kbm on 2009-10-01
Thanks so much, that explained it quite well.  I had read your other post (KDE4 Phonon and PulseAudio), which is great - thanks for all the info, but I still wasn't getting that Pulse had already grabbed control of the card (or that I was tinkering with Phonon to be honest).

---

