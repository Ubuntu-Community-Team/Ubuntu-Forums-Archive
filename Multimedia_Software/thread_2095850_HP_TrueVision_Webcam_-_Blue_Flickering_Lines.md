---
title: "HP TrueVision Webcam - Blue Flickering Lines"
date: 2012-12-18
forum: Multimedia Software
---

### Post by caeso on 2012-12-18
I am not sure how to troubleshoot this. The webcam, in Skype and Cheese, shows constant flickering blue lines.

I do know that the device is a "HP TrueVision HD", but not much more than that. I am using an HP Envy 14.

Any suggestions?

---

### Post by caeso on 2012-12-26
/bump.

I've been working on this and still no resolution.

---

### Post by caeso on 2013-02-07
/bump

I tried following several other threads that instruct to do things like:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype.real
```

And run that file, and skype loads and whatnot, but it still does the same thing.

What's odd is when the video preview first loads, for the first half second or so the video looks fine, then it starts "filtering" or whatever and it's filled with tons of crappy horizontal blue lines.

The same thing happens in Google hangouts.

Cheese looks great, the video is glorious.

What the heck?

---

### Post by xc3RnbFO8P on 2013-02-07
How bad is it, can you show us screenshot?
Have you tried more light?

---

### Post by gonzobilbao on 2013-05-25
Probably this thread was dead long ago, anyhow, I have the same problem, with my HP envy4, using linuxmint 14 (based on quantal) , 64bit, on it. Lsusb prints

```
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 

```

Gstreamer-properties prints:

```


(gstreamer-properties:9418): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:9418): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc

```
I believe it MIGHT have something to do with it being a 64bit system. Previously I had a 32bit system on my computer, and I don' t remember it to have poor video quality. Something I have noticed is that the video shows even more scrambled when there is not much light there. I believe this truevision cams have some light compensation thing, so when there is not much light they somehow enhance the illumination. Anyhow, I have been working on this for a long time now with no results, any help?

THanks!

---

