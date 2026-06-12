---
title: "Alsa Control Question (Exponential Volume)"
date: 2008-11-20
forum: Multimedia Software
---

### Post by ZeroTruths on 2008-11-20
I've been having this problem for a while now, and decided to look into it. What happens is that my volume control behaves in an 'exponential' way, meaning that the regular, noticeable volume difference occurs within the last 1/3 to 1/4.

I ran **amixer** and go this output:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [off]
  Front Right: Playback 65536 [100%] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]

```

I noticed that both controls have a 'Limits' value, and I was wondering if there was any way for this to be changed (to something like 43691-65536).
Is there some command within alsa to do this?

---

### Post by humphreybc on 2009-05-24
I too would like to know how to change it to Linear instead of exponential... seems so silly as my volume rarely goes below 75% because it becomes almost inaudible!

---

