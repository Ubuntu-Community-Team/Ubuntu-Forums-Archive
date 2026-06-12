---
title: "Could I get some help recording from S/PDIF with a Creative X-Fi?"
date: 2014-08-23
forum: Multimedia Software
---

### Post by Aaron_Altman on 2014-08-23
The model number is SB0460.  I can start JACK in QjackCtl with Input set to hw:XFi, hw:XFi,0 (Front/WaveIn) or hw:XFi,4 (IEC598).  None of those settings lead to being able to record sound in Audacity.

lspci -v:

```
08:00.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi XtremeMusic
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at ec00 [size=32]
        Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: snd_ctxfi
```

aplay -l:

```
card 7: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
... on to 256

card 7: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
...

card 7: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
...

card 7: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
...

card 7: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

amixer -c 7:

```
altie@altiemain:~$ amixer -c 7
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 176 [69%] [-20.00dB] Capture 256 [100%] [0.00dB]
  Front Right: Playback 176 [69%] [-20.00dB] Capture 256 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Digit-IO',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Digital',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 196 [77%] [-15.00dB] [on]
  Front Right: Playback 196 [77%] [-15.00dB] [on]
```

Any help would be much appreciated!  Cheers.

---

