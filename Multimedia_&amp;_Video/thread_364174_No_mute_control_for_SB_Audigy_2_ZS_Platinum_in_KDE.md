---
title: "No mute control for SB Audigy 2 ZS Platinum in KDE"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by jsteve54302 on 2007-02-17
*Crossposted from Hardware & Laptops

This has been bugging me since I started using kubuntu several weeks ago I cannot get the sound to mute through any means (multimedia keyboard button, kmix (it only has a mute button for the headphones and cd), or using the amix toggle, mute/unmute commands - see screenshot). I have even tried setting the PCM and Master channels to nocap, just in case something had put them into capture mode. Muting works fine in my ubuntu/Gnome environment (with kdm set as the desktop manager), but only if I log in with a Gnome session.  But when I log in to a KDE session on my ubuntu installation or log in to my kubuntu session (which does not have Gnome installed), the mute buttons disappear and the keyboard mute button stops working.  Because of this odd behaviour, i strongly suspect a bug in KDE, but I am wondering if anyone has encountered (and fixed :) ) this problem.

I am using:

Kubuntu 6.10 Edgy Eft, full KDE 3.5 installed
Creative Audigy 2 ZS Platinum (SB0350)

and here is what I have tried to get the mute to work:

This (together with the fact that a Mute/Unmute splash is displayed when I press the mute button) shows that the keyboard settings are sane.
```
john@john-desktop:~$ xev   
KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  77  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   1   0   0   0   0   0   0   0   0   0   0   0

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0x1a5, subw 0x0, time 2924338347, (146,134), root:(158,576),
    state 0x0, keycode 160 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```These commands don't produce errors, but they also don't mute the sound.
```
john@john-desktop:~$ amixer set PCM toggle
john@john-desktop:~$ amixer set Master toggle
```These tell me that the mute/toggle function aren't supported.
```
john@john-desktop:~$ amixer set PCM mute
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] Capture 80 [80%]
  Front Right: Playback 100 [100%] Capture 80 [80%]
john@john-desktop:~$ amixer set PCM unmute
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] Capture 80 [80%]
  Front Right: Playback 100 [100%] Capture 80 [80%]
``````
john@john-desktop:~$ amixer set Master mute
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 25 [25%]
john@john-desktop:~$ amixer set Master unmute
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 25 [25%]
``````
john@john-desktop:~$ amixer set PCM nocap
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] Capture 80 [80%]
  Front Right: Playback 100 [100%] Capture 80 [80%]
john@john-desktop:~$ amixer set Master nocap
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 25 [25%]
```This isn't exactly critical, but I would be grateful for any information on how to fix this.

---

