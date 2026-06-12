---
title: "Audio randomly stopped working"
date: 2008-11-21
forum: Multimedia Software
---

### Post by TUOggy on 2008-11-21
Okay, so everything was working fine, and then I get on my computer this evening, and I have no audio.  I tried following the audio troubleshooting guide, and it didn't help, so here I am.

here is the applay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

in a lspci -v | less, I didn't hav "Audio Controller" but I had the following entry

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Sony Corporation Device 815b
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at d400 [size=256]
        I/O ports at d000 [size=64]
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```

I'd really like to have my sound back.

What must I do without completely reinstalling Ubuntu?

edit
Forgot to mention.  I'm using Ubuntu 8.10
/edit

---

### Post by TUOggy on 2008-11-21
okay... strange thing just happened...

I started playing with my volume controllers...

didn't really do anything except play with the sliders a little bit and then the music started playing.

I'm really at a loss...   I didn't do anything and they started working again.

---

