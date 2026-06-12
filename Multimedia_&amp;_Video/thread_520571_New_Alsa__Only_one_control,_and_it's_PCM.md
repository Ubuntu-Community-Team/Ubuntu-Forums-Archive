---
title: "New Alsa:  Only one control, and it's PCM"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by DizzyTech on 2007-08-08
I've had this problem before, but I've decided to solve it once and for all.  You see, I installed a new ALSA on Feisty's kernel.  More recently, I installed Gutsy's kernel.

The ALSA that I installed and the one installed by Gutsy's keren lare both the module for 1.0.14 final.  In this version, I have a bug:  the "Master" volume no longer takes effect, and only PCM has effect, but it gets really loud (I mean **really**) at anything over 75%, and dead quite under 50%.  Not much room for happiness.

This problem originally spouted by manually installing a new ALSA to fix crackliness and sound accuracy problems, but I rolled back by reinstalling my kernel and alsa-sound.

Now, I have the Gutsy kernel, and things are faster, but sound is screwy, so I've decided to fix it.  I've played around with things a little, and am now loading my sound card with the hp-laptop mode (more about that later), which provides me with great configuration options, including Headphone, Mic Gain, Speaker, PCM1, and PCM2, however, none of them work except PCM1.

My main question is, without rolling back ALSA, how do I go about fixing this?

Here's my sound card info:
**aplay -l**:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**lspci -v**:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

**GRUB kernel options**:
```

rootflags=data=writeback noacpi apm=on noapic irqpoll noirqdebug

```

My computer is a Compaq Presario V5204NR, release approximately a year ago.

---

### Post by DizzyTech on 2007-08-08
Bump.

---

### Post by DizzyTech on 2007-08-09
Hello...

---

