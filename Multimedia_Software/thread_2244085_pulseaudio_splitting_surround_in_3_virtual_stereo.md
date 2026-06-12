---
title: "pulseaudio splitting surround in 3 virtual stereo"
date: 2014-09-13
forum: Multimedia Software
---

### Post by biervat2 on 2014-09-13
I want to split a 5.1 sound card into 3 virtual stereo cards. I changed the following in default.pa:
```
removed:
load-module module-udev-detect
load-module module-detect

add:

load-module module-alsa-sink device=hw:0 sink_name=alles channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channels=6 sink_properties=device.description="overal"
load-module module-remap-sink sink_name=keuken master=alles channels=2 master_channel_map=front-left,front-right channel_map=front-left,front-right sink_properties=device.description="Keuken"
load-module module-remap-sink sink_name=slaapkamer master=alles channels=2 master_channel_map=rear-left,rear-right channel_map=front-left,front-right sink_properties=device.description="Slaapkamer"
load-module module-remap-sink sink_name=badkamer master=alles channels=2 master_channel_map=front-center,lfe channel_map=front-left,front-right sink_properties=device.description="Badkamer"
```


the 'alles'-sink works on all channels, but the 'keuken', 'slaapkamer' and 'badkamer' sink always play through the front-center,lfe channels
When I add remix=no to the remap-sinks, the channels are correct but there's only one sink at a time that works.

---

