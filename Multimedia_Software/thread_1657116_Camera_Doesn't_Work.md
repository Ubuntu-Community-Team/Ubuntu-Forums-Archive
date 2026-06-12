---
title: "Camera Doesn't Work"
date: 2010-12-31
forum: Multimedia Software
---

### Post by WilsonMESS on 2010-12-31
Hi, my camera seems not working. Cheese freeze at opening, so I go to the multimedia support using gstreamer-properties, and here's the result:
```
wilsonmess@WilsonMESS-EeePC:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc1]

```
Any ideas? Thanks!

---

### Post by no2498 on 2011-01-02
open a terminal type webcam click enter
it should install a cam grabber 

also look in your package manager 
search for gstreamer

you need the good, bad, ugly, and 10 installed

retry gstreamer-properties

---

### Post by WilsonMESS on 2011-01-15
> **no2498 said:**
> open a terminal type webcam click enter
it should install a cam grabber 

also look in your package manager 
search for gstreamer

you need the good, bad, ugly, and 10 installed

retry gstreamer-properties

Still the same result. Do you mean install *ALL* packages name from "gstreamer-*"?

---

### Post by BicyclerBoy on 2011-01-16
Try guvcview

This package is involved with development of webcam drivers in the kernel. 

Cheese is almost useless.

install ubuntu-restricted-extras package

---

### Post by no2498 on 2011-01-16
wxcam works  good if you use 32 bit

[http://wxcam.sourceforge.net](http://wxcam.sourceforge.net)

---

### Post by BicyclerBoy on 2011-01-16
Is this a netbook Asus Eee PC 1005PE ?

Ubuntu netbook edition is reported to work well with this netbook

---

### Post by no2498 on 2011-01-17
open a terminal type lsusb click enter
post the output here
if you see a rico cam you need a driver for it

---

### Post by WilsonMESS on 2011-01-20
> **BicyclerBoy said:**
> Is this a netbook Asus Eee PC 1005PE ?

Ubuntu netbook edition is reported to work well with this netbook

Well I don't like its user interface, it looks awkward...(Personal Opinion)

---

### Post by WilsonMESS on 2011-01-20
> **no2498 said:**
> open a terminal type lsusb click enter
post the output here
if you see a rico cam you need a driver for it

no rico cam found

---

### Post by WilsonMESS on 2011-01-20
> **BicyclerBoy said:**
> Try guvcview

This package is involved with development of webcam drivers in the kernel. 

Cheese is almost useless.

install ubuntu-restricted-extras package

installed, and...?

---

### Post by BicyclerBoy on 2011-01-20
run
gstreamer-properties

Try a test with v4l & v4l2 lib interface..

---

### Post by no2498 on 2011-01-20
? do you have a fn key
if yes try the fn+f4 at the same time
did the cam light come on
if yes try cheese again

---

### Post by no2498 on 2011-01-20
think he needs to try the fn+f4 key's at the same time
just to turn the cam on first

---

### Post by no2498 on 2011-01-20
think he needs to try the fn+f4 key's at the same time
just to turn the cam on first

---

### Post by WilsonMESS on 2011-01-20
> **BicyclerBoy said:**
> run
gstreamer-properties

Try a test with v4l & v4l2 lib interface..

"No device found" again

---

### Post by WilsonMESS on 2011-01-20
> **no2498 said:**
> think he needs to try the fn+f4 key's at the same time
just to turn the cam on first

every pc notebook should have function keys, dude.
fn+f4 represents change screen resolution here, since the screen resolution of my netbook isn't "normally defined". and no separate key for cam on/off.

---

### Post by no2498 on 2011-01-21
[http://www.google.com/search?client=opera&rls=en&q=netbook+Asus+Eee+PC+1005PE+webcam&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=netbook+Asus+Eee+PC+1005PE+webcam&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)


netbook Asus Eee PC 1005PE webcam


if the link dont work put that in google

---

### Post by no2498 on 2011-01-21
find and install xawtv
it loads a grabber too
ive had to do it myself a few times to get my cam working

---

