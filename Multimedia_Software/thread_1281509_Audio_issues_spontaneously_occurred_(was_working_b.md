---
title: "Audio issues spontaneously occurred (was working before)"
date: 2009-10-03
forum: Multimedia Software
---

### Post by grimreaperwithalawnmower on 2009-10-03
Hi there, after having the problems with X that users with Nvidia motherboards have traditionally experienced, I realised that my issues were likely to be my own idiocy, so I reinstalled Jaunty and installed all the right drivers and hey presto, everything was fine, including sound.

Then, during the week, I had to boot up Windows for work and everything was fine there too.  The the next time I booted up Ubuntu I'd lost sound.  I say lost, but what I get instead of sound is static-like noise.  I know it's not my speakers because they still work on Windows (and spew out noise on Ubuntu), and Ubuntu isn't and never has had issues recognising my sound card.

I've gone through the documentation pages and the troubleshooting there is mostly for those who haven't ever had any sound, so I'm stumped as to what the cause is and a potential solution, so any advice would be greatly appreciated (blaming Windows may make me feel a bit better, but it doesn't solve the problem!

Cheers
Matt

terminal outputs:

```
matt@floyd:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v | less
.....
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
        Subsystem: Acer Incorporated [ALI] Device 0137
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fea78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

Any other info, give me a shout.  Thanks in advance  MK  x

---

