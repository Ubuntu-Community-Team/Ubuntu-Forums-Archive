---
title: "|Sound stuttering on Acer TravelMate 4200 laptop"
date: 2013-02-24
forum: Multimedia Software
---

### Post by pc.maint on 2013-02-24
Having searched all the forums and extensively on Google, I have not yet found a solution to this annoying problem...

When playing any kind of media from any source, after a short time, the output stutters until the mouse is moved. Constant mouse movement prevents the problem. Stop the mouse and within a short time, the stuttering starts again.

This system worked fine with Ubuntu 10.04. A clean install of 12.04.2 with all the latest updates gives rise to this problem. Also does the same with UbuntuStudio and ArchLinux.

I have two identical laptops doing the same thing.

System details:

Acer TravelMate 4200 V3.24
3.2.0-38-generic-pae GNU/Linux i686 SMP Enabled

ALSA:
Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25
snd_hda_intel

Audio device:
Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

Modprobe options (Sound related):
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=generic

Any ideas would be appreciated as my arm is getting tired from waggling the mouse.....

---

