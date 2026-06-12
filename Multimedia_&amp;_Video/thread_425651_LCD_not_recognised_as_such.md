---
title: "LCD not recognised as such"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-04-27
I got a new 19" flatscreen TFT monitor recently and have been very disappointed in the display quality. Images on websites often display extremely pixelated and washed out and text on many pages overlaps itself, among other things like ghosting of images and text. 
I've tried to tell my xorg.conf that I'm using an LCD monitor but if I change the line
```
 
Option         "ConnectedMonitor" "CRT, TV"

```

to 

```
 
Option         "ConnectedMonitor" "DFP, TV"

```

I get no output to the monitor. Same if I use DFP-0 or DFP-1. 
Does this setting require that the monitor be connected via a DVI cable?

---

### Post by reclusivemonkey on 2007-04-28
Please post;

[LIST]
[*]Monitor make and model
[*]Graphics card make and model
[/LIST]

and attach your xorg.conf

---

### Post by pickarooney on 2007-04-29
Monitor = Nitstek MJ9BNK
GFX card = NVIDIA GeForce 6200 TurboCache

---

### Post by reclusivemonkey on 2007-04-29
I would recommend getting the monitor to work on its own first rather than trying to acheive a dual screen setup straight away. I would comment out "UseModes" sections in monitor, uncomment DPMS, and the comment everything after DefaultDepth up to SubSection "Display". I suspect the modeline is giving you problems. I would then check that your TV does indeed support 800x600.

---

### Post by pickarooney on 2007-05-21
Just bumping this in case anyone knows why the monitor is only recognised as CRT and not DFP (TV works perfectly). 
Does DFP only refer to an LCD monitor with a DVI cable?

---

