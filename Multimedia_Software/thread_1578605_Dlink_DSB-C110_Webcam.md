---
title: "Dlink DSB-C110 Webcam"
date: 2010-09-20
forum: Multimedia Software
---

### Post by kerryhall on 2010-09-20
I have a Dlink DSB-C110 Webcam. lsusb gives me 
Bus 002 Device 012: ID 06a5:d800 Divio Chicony TwinkleCam

So it detects some camera. Tried gstreamer-properties in order to test it out, but there is no /dev/video0.

How do I get this working?

Karmic

---

### Post by kerryhall on 2010-09-26
Bump.

---

### Post by kerryhall on 2010-09-30
Bump. I really would like to get this working.

---

### Post by kerryhall on 2010-10-05
Bump.

---

### Post by no2498 on 2010-10-06
see if this helps put it in a terminal

lsmod | grep video

---

### Post by kerryhall on 2010-10-06
No results from that command. I would like to try installing gspca. Tried building it with no luck. [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

