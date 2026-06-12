---
title: "How to switch right to left speaker in 11.04?"
date: 2011-07-24
forum: Multimedia Software
---

### Post by kenny_lex on 2011-07-24
I do not find any settings to switch the stereo output in Ubuntu, just now my speakers is placed so right speaker stands to the left and I can not move them just now.

How do I do, I use Ubuntu 11.04.

---

### Post by Cousjava on 2011-08-27
Edit ```
/etc/pulse/default
``` with your chosen text editor. Add in the lines

```
load-module module-remap-sink sink_name=reverse-stereo master=0 channels=2 master_channel_map=front-right,front-left channel_map=front-left,front-right
set-default-sink reverse-stereo
```

You may have to restart PulseAudio or your computer for this to take effect.

---

