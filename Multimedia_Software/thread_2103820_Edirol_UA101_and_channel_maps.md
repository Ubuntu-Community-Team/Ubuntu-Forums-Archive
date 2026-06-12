---
title: "Edirol UA101 and channel maps"
date: 2013-01-11
forum: Multimedia Software
---

### Post by kelcey_s on 2013-01-11
Hello everyone,

After sorting this sound card so it works at all, a process involving manually telling Pulse Audio to use it by adding the following lines to /etc/pulse/default.pa

```
load-module module-alsa-sink device=hw:0,0
load-module module-alsa-source device=hw:0,0
```

Because, for some reason, the UA-101 doesn't show up as an alsa device despite showing up when you type:

```
aplay -l
```

I now have the following problem...

My sound card is treated like it is a 7.1 device, which it is not. My stereo speakers are plugged into the monitor outputs (where every channel gets sent out to right and left) which I need to do in order to hear anything on a DVD. But this means that when listening to a stereo output it comes out on every channel, not just channels 1 and 2.

Is there any way to specify a custom channel map to make stereo outputs only go to channels 1 and 2?

Any help would be greatly appreciated.

Kelcey

---

