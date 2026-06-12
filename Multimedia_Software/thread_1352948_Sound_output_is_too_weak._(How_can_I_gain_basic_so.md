---
title: "Sound output is too weak. (How can I gain basic sound output level?)"
date: 2009-12-12
forum: Multimedia Software
---

### Post by amoriguchi on 2009-12-12
Hello all,

I have troubled with newly installed ubuntu 9.10 about sound output is too weak.
I've read "[COLOR=navy]_**[SIZE=4][B]Comprehensive Sound Problem Solutions Guide** v0.5e"[/SIZE][/B]_[/COLOR] and confirmed the alsa is ok.
Also I set all alsamixer's parameters maximum and System->Sound->Output volume "Maximum."
Off cource, my PC's volume is maximum.
But still I barely hear the sound but subtle beat.

Is there any way to gain basic sould level?

My test command output is following.
**aplay -l**
```
dokodemo@dokodemo-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dokodemo@dokodemo-laptop:~$
```**lspci -v**
```

   *
   *
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at da080000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```**Alsa support**
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

**PC**
TOSHIBA [SIZE=2]dynabook SS S31

Best regards
[/SIZE]

---

### Post by h3lLx0x on 2009-12-12
I also got the same problem with you. The sound was so low while I had maximum my volume.

My test command output is following.

**aplay -l**

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**ispci -v**

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 82ea
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

---

### Post by fishbulb1022 on 2009-12-14
If you are dual booting with windows, and it works fine in windows, make sure you do not leave the sound muted in windows when you shut down. It sounds stupid but it gave my brother problems for months before he figured it out.

---

### Post by VertexPusher on 2009-12-14
Every time PulseAudio starts up, it resets ALSA mixer settings to whatever it deems OK. Unfortunately most of the time the result is not OK. Unfortunately there is no configuration option to stop PulseAudio from messing with ALSA's volume levels.

Yes, it's a bug, and it has been reported about a year ago. I'm sure we'll see a fix in 2011. If you don't want to wait that long, remove PulseAudio.

---

### Post by h3lLx0x on 2009-12-14
> **VertexPusher said:**
> Every time PulseAudio starts up, it resets ALSA mixer settings to whatever it deems OK. Unfortunately most of the time the result is not OK. Unfortunately there is no configuration option to stop PulseAudio from messing with ALSA's volume levels.

Yes, it's a bug, and it has been reported about a year ago. I'm sure we'll see a fix in 2011. If you don't want to wait that long, remove PulseAudio.

How can I remove PulseAudio. Are you sure this is the problem? because I already did it and I don't hear ANYTHING and I reinstall my ubuntu.

---

### Post by amoriguchi on 2009-12-15
I also followed the instraction listed [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller#Method%20A:%20%20Rebuild/install%20alsa-modules](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller#Method%20A:%20%20Rebuild/install%20alsa-modules) , but still no good.
About rebuilding  alsa-driver from source, I even couldn't do make successfully.
In the other methods, I have done successfully the instruction, but the result is no effect on the problem.

After reading suggestion about  pulseaudio, I removed pulseaudio.
But in that case, the sound output cutt off and silent.  
System -> Preference -> sound doesn't work and the speaker icon disappeared.

How can I remove pulseaudio without disabling sound?

---

