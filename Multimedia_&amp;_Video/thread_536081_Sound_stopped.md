---
title: "Sound stopped"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by toasterboy1 on 2007-08-27
Problem:
Sound stopped working anywhere. No sound from amarok, websites, notifications. Was working previously. Still works under Windows.

Background:
Compaq Presario V6133CL Notebook
Kubuntu Fiesty AMD 64
Onboard soundcard

aplay -l output:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer:
Max volume on master and pcm.
IEC958 off.

User membership:
adm, dialout, cdrom, floppy, audio, dip, video, plugdev, scanner, netdev, lpadmin, powerdev, admin

Things done between time audio was working and when it stopped:
Used Klitz script to install Swiftweasel with flash, sound, and java.
Installed Swiftdove from .deb
Updated kde through synaptic.

Things I have tried:
Reinstalled alsa related packages from synaptic. Ran kmix and alsamixer to check for muted channels. Tried different audio devices under system settings sound system.

Thanks

Update:
Downloaded newest alsa-driver file. Made modules. Added snd_intel_8x0 to /etc/modules.

---

### Post by mariopiu on 2007-12-25
pls say how did u fix that i have the same sound card and suddenly it stopped workin....i think after i installed flash plugin for firefox
if someone else knows whats happening pls tell me how to fix this
tnx

---

