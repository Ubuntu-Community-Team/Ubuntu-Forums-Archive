---
title: "Audio Stopped Working"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by onepapership on 2007-12-24
I am running a dual-boot gutsy/vista system on an hp pavilion dv2000. My sound worked fine for the first 3 weeks I had the computer, and about 5 days ago I performed an update in gutsy and it stopped (still works fine in vista). There is no audo, no system sound, nothing. I have tried every single thing I've found on this forum, short of actually reinstalling Ubuntu. I have checked all of my audio settings in alsamixer and volume controls, nothing is muted;  I have uninstalled and reinstalled the alsa packages; I have recompiled and installed the alsa packages; I have edited /etc/modules and /etc/modprobe.d/alsabase to reflect my sound card and various options. I am currently downloading and re-installing my current kernel and selected other packages in what I think may be my last effort. Do I have to accept no sound in Ubuntu? It's ridiculous, but so is having to reinstall just to get sound working (again). Please help if you can.

uname -a:
Linux Abbey 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cd
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

amixer:
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Mono:
  Front Left: Playback 35 [81%] [-12.00dB] [on]
  Front Right: Playback 35 [81%] [-12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'LineIn',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Ext Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 23
  Front Left: 22 [96%] [33.00dB] Playback [on]
  Front Right: 22 [96%] [33.00dB] Playback [on]
Simple mixer control 'Int Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 23
  Front Left: 23 [100%] [34.50dB] Playback [on]
  Front Right: 23 [100%] [34.50dB] Playback [on]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]

---

