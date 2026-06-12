---
title: "no PCM or Master in alsamixer"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by teh_luke on 2008-01-31
Hi,

As you can see below I have no PCM or Master volume control with alsa-mixer (or gnome-volume-control).
The working ones are Analog Front, Analog Rear, Analog Center/LFE.
I have 5.1 with Soundblaster Audigy 2 SE working so far, but i'd like to be able to have a volume control in gnome-volume-control which effects all output. If i was able get it into g-v-c there would be no problem binding it to the keys on my keyboard.
How can I get this to work?
Please tell me if more information is needed.


Thanks in advance.

```

$ amixer 
Simple mixer control 'Line in',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB] [on]
  Front Right: Capture 207 [81%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB] [off]
  Front Right: Capture 207 [81%] [0.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 1 [0%] [-51.50dB]
  Front Right: Playback 1 [0%] [-51.50dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 209 [82%] [0.50dB]
  Front Right: Playback 209 [82%] [0.50dB]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 209 [82%] [0.50dB]
  Front Right: Playback 209 [82%] [0.50dB]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 209 [82%] [0.50dB]
  Front Right: Playback 209 [82%] [0.50dB]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Digital Capture Source',0
  Capabilities: enum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: enum
  Items: 'Line in' 'Mic in'
  Item0: 'Line in'

```

---

### Post by teh_luke on 2008-02-02
bump

---

### Post by teh_luke on 2008-02-04
bump

---

