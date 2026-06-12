---
title: "Microphone disabled.  Can't enable."
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by Seine on 2007-04-16
Hello

My Microphone input has always been disabled since I first installed Dapper (I'm in Edgy now). I've done some googling to try to fix this but nothing has helped.

I've tried the three "temporary fixes" in [this bug thread]("https://bugs.launchpad.net/ubuntu/+bug/80531") and none of them worked.

My machine is an HP Pavilion dv5000 laptop. It has a single mic input on the side. I'm not sure how to find out more about my sound chip. The Sound Preferences applet (gnome) shows it as "HDA Intel"

Here's my alsamixer:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29828&stc=1&d=1176718210[/IMG]

The MIC input volume cannot be modified. I can only disable MIC by enabling Line and visa versa (its a toggle).

vumeter show no input signals.

The output of amixer is```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 23 [77%] [on]
  Front Right: Playback 22 [73%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [on]
  Front Right: Capture 14 [100%] [on]

```

Any help would be greatly appreciated!

Thanks
Jem

---

### Post by jjalocha on 2007-04-16
You can find out what sound card you have with:

```

$ aplay -l

```

```

$ lspci

```

---

