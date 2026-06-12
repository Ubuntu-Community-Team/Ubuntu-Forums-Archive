---
title: "Terrible sound quality, volume is not a solution"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by Wiseman1024 on 2007-06-23
I'm experiencing terrible sound quality with Feisty. Everything sounds terribly distorted and low quality. I have internal AC'97 sound provided by an Asus P4S800D motherboard (SiS 655FX chipset) with a SiS SI7012 sound card with an Analog Devices AD1980 sound chip.

I'm using, as automatically detected and recommended by the ALSA matrix, the snd_intel8x0 module.

Sound volume is set to 100% Master, 74% PCM as suggested in some threads, but it's not a solution; it still sounds terrible. Further lowering sound volume makes sound inaudible, and still terrible quality (just it's difficult to notice it, or anything at all). I've played with alsamixer disabling everything but master and PCM, and enabling everything to an audible level, and juggling all other options, without success.

Furthermore, sound volume is low, unless set to very high levels (80% master and PCM). On Windows, sound volume is always much higher at just 50% master and PCM, and sound is crystal clear, even at 100% master and PCM.

(I'm not using any asound.conf script; tried many without change; it's probably not a problem with ALSA but a problem with snd_intel8x0.)

Any ideas? Thank you in advance.

lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GS (rev a2)

```

lsmod | grep snd:
```
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
ac97_bus                3200  1 snd_ac97_codec
soundcore               8672  1 snd
```

---

### Post by WinterWeaver on 2007-06-23
I'm having the same problems. I've tried the solutions on other threads, with no success. I hope there is a solution to this soon.... -_-

WW

EDIT: btw... for me it's been bad quality since Edgy, but it seems as though its worse in Feisty. Hope it doesn't keep on declining in coming releases. I remain positive that it will be awesome :P

---

