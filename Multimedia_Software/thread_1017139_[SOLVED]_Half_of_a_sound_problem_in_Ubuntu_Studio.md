---
title: "[SOLVED] Half of a sound problem in Ubuntu Studio"
date: 2008-12-20
forum: Multimedia Software
---

### Post by matthanley on 2008-12-20
I have a fresh install of Ubuntu Studio 8.10 on my fairly old computer (P4, 1GB).  The computer has onboard sound, but I'm using my SB Audigy 2 ZS.

I'm having trouble getting sound on some applications, but not others.  For example, Rhythmbox and Totem both give sound (although Rythmbox sounds overmodulated), but Firefox, Audacious and gfceu do not.

I've tried most of the suggestions on [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting"), but it hasn't really gotten me anywhere.

Here's the relevant output:
```
aplay -l
``` gives me this (I deleted some "Subdevices" lines to cut down the length, but they're in the output):
> **** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  ...
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  ...
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
find /lib/modules/`uname -r` | grep snd
``` gives me a few pages of results including this:

> /lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko


The output of ```
lspci -v
``` included these two sections:

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio C
ontroller (rev 05)
        Subsystem: Dell Device 0115
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e800 [size=256]
        I/O ports at ef00 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Device 2002
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at df00 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

And ```
cat /proc/asound/modules
``` showed this:

>  0 snd_intel8x0
 1 snd_emu10k1


I tried every different output plugin for Audacious, and none of them gave me any sound.  I can't find anywhere in Totem or Rhythmbox (the two apps that give me sound right now) to configure the sound output, so I can't figure out where the sound from those is going on its way to the speakers.  There are a ton of different sound management programs on here, so I don't know if they're all fighting each other or what.  I've played with alsamixer and I know that nothing is muted or turned down there, and I haven't been able to find anything in the Pulse Audio configuration that does any good.

I haven't bothered to play with Ardour or any sound production apps yet because of all this, so I don't know how that would go, either.

Sorry for the long post.  Any help would be greatly appreciated.

---

### Post by matthanley on 2009-01-06
It looks like PulseAudio was the problem, and after reading up on it a bit, it doesn't look like it has much to offer me.

I was able to fix the problem by following the steps in the first post of this thread: [Fix all PulseAudio-related issues in 2 minutes]("http://ubuntuforums.org/showthread.php?t=885437").

---

