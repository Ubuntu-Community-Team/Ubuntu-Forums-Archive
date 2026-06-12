---
title: "Sound Card Stopped Working"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Asheboy on 2008-08-01
My sound card has stopped working after a recent restart. I've tried the  Comprehensive Sound Problem Solutions Guide but it ended up with telling me to make a topic.

I've got a

```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Foxconn International, Inc. Unknown device 0d15
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

I don't really know what other information you need. My ALSA driver is snd-hda-intel.

---

### Post by montgoss on 2008-08-03
Try the following command:
```
sudo modprobe snd-hda-intel
```

---

