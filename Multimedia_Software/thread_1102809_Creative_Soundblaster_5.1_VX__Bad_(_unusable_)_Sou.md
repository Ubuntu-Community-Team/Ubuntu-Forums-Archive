---
title: "Creative Soundblaster 5.1 VX : Bad ( unusable ) Sound"
date: 2009-03-22
forum: Multimedia Software
---

### Post by benjjo on 2009-03-22
Hi, im trying to get my Creative Soundblaster 5.1 VX to work but to no avail. 
I have tried what i can on this page: [Ubuntu_Forum1]("https://help.ubuntu.com/community/SoundTroubleshooting")
And this: [Ubuntu_Forum2]("http://ubuntuforums.org/showthread.php?t=205449")

My sound is definitely on, as i seem to get a scratchy piercing sound with a hint of the actual audio in the background. The card does work perfectly well in another operating system that i wish to remain nameless. 

From what i can tell, my sound card is recognised and it is using the correct module i.e.

```


benjo@nixbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
benjo@nixbox:~$

benjo@nixbox:~$ lspci -v | less
.
.
.
02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Device 1004
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at a000 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: CA0106
        Kernel modules: snd-ca0106
.
.
.

```

This is the card that i have: [Sound_Card]("http://www.soundblaster.com/products/product.asp?category=1&subcategory=207&product=17510&listby=brand")

It would seem that the "VX" model may be unsupported hardware in the world of Linux. Although, i have found a guy that claims to have gotten it to work on another Linux distro, here: [Alsa_Project]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011333.html"). Would anyone know how to transfer this information to Ubuntu?

According to that post, my card is using the right module. The ALSA project has a different idea :[ALSA_Project2]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs"), that page recommends that the emu10k1 chipset module should be used. 

It's a little confusing when ALSA would recommend a different chipset to the one that is suggested in the link above. I would like to try the emu10k1 module as the ALSA recommends, but i don't know how to do that. I assumed that you would just "sudo modprobe snd-emu10k1", but nothing seems to happen. 

FYI
```

benjo@nixbox:~$ find /lib/modules/`uname -r` | grep snd-emu10k1
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
benjo@nixbox:~$ 

```

Any help is appreciated.


Ubuntu 8.10
2.6.27-11-generic

---

