---
title: "Yet another sound after upgrade issue"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Damanther on 2008-05-21
I am having similiar problems. Sound worked fine under gutsy, but ever since the upgrade to hardy I haven't heard a peep from my speakers.

It is an hp m7750m with integrated audio. I'm running th 64bit hardy version.

aplay -l shows that the card exists.

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: pcsp [pcsp], device 0: pcspeaker [pcsp]
Subdevices: 1/1
Subdevice #0: subdevice #0

lspci | grep Audio shows it as

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I have ths snd_hda_intel module loaded in alsa

The only error I see in the logs is this from dmesg:

hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

Does anyone have a clue how to help us out?

Non of my apps complain about not having or connecting to an output device, but I get NO sound.

---

### Post by Yellow Pasque on 2008-05-21
Try:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

