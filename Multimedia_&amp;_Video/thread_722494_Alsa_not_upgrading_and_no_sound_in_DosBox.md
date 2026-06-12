---
title: "Alsa not upgrading? and no sound in DosBox"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by NFITC1 on 2008-03-12
I've been having problems with programs not working well with ALSA and not having MIDI support. More specifically, when I load DosBox 0.72 (compiled from source) I get this:
```
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
CONFIG:Loading primary settings from config file dosbox.conf
MIDI:Can't find device:alsa-oss, finding default handler.
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss

```
Gutsy comes with ALSA version 1.0.14-1 and now the 1.0,16 is out so I dl'ed all those packages and compiled and installed them. But Synaptec still reports alsa-base, alsa-oss versions as 1.0.14-1 (may or may not mean anything). So now every time I try to load a program in DosBox that has sound it crashes with a Segmentation Fault.
aconnect -o says
```
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 128: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '
```
aplay -l says:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I'm not sure what else I'd need to report. Anyone know how to help?

---

### Post by Skerit on 2008-03-29
I'm wondering about this, too. Although I'm running the hardy beta

---

