---
title: "No sound with 8.10 and built in sound card"
date: 2008-11-04
forum: Multimedia Software
---

### Post by gonzoateafly on 2008-11-04
Howdy all,

First, let me say I'm a complete beginner to both kubuntu and even linux.  I'm generally good with computers, but a lot is very unfamiliar to me, so bare with me. :)

I'm running into sound isues.  I get the feeling I'm not the first to experience issues with my card, based on the searching I've done, but it sounds like others have theirs working... I just can't seem to join the club!
Here are the values I have from what looks like the standard questions asked:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
james@james-desktop:~$

```

and...
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)                                                          
        Subsystem: Intel Corporation Device 0707                                
        Flags: bus master, fast devsel, latency 0, IRQ 22                       
        Memory at 54300000 (64-bit, non-prefetchable) [size=16K]                
        Capabilities: <access denied>                                           
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel  

```

From there, I'm stuck.  I tried a very complicated solution found here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I took that to the point of just before the phrase "Manually Specify Module Parameters", after the reboot.  I ran dmesg... and didn't see the string snd_... but I'll be honest, there was a lot, I could have missed it.

After that point, I was able to get the codec, which I'll list below, but was stuck trying to find the ALSA configurations.
Codec: SigmaTel STAC9220D/9223D A2

This is the most I can provide, beyond this point, I'm frankly a little lost.  All I want is to have sound so I can listen to music/watch dvd's through kubuntu.  I'm trying to transition myself off Windows, and I thought that would be a good way to start and become familiar with the system... but so far it's been a little frustrating.

Any help would be GREATLY appreciated.  :)

Thanks,
Gonzo

---

### Post by gonzoateafly on 2008-11-04
Alright... I don't know if I fixed it from going through that long tutorial and the other odds and ends I did, but I just discovered that the sound is dependent on 3 different slider bars (for some reason)... so after cranking them all up, I can hear.  :)

Thanks anyway!

---

### Post by bsnapp on 2008-11-26
Thanks!  This was the case with me as well.  I had all the driver installed correctly, and it just came down to cranking up the side, PCM, and Master levels in alsamixer.

---

