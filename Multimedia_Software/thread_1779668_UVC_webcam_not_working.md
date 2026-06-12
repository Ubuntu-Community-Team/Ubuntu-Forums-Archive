---
title: "UVC webcam not working"
date: 2011-06-10
forum: Multimedia Software
---

### Post by someitalian123 on 2011-06-10
My webcam is apparently supported, it's on the list, it's a Logitech Webcam C210

 [http://www.ideasonboard.org/uvc/#introduction](http://www.ideasonboard.org/uvc/#introduction)

I tried cheese and it didn't work, I tried skype and it didn't work, I tried gstreamer-properties and I couldn't even get it to start, I get this

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

Why doesn't my webcam work? why doesn't gstreamer-properties work?

I tried lsusb to see if it was listed, it's listed as

Bus 001 Device 002: ID 046d:0819 Logitech, Inc.

Linux 2.6.26     and newer includes the Linux UVC driver natively right? What am I doing wrong? Any help would be greatly appreciated.

---

### Post by no2498 on 2011-06-11
open a terminal type dmesg click enter

after it stops install xawtv try the cam in it


open your package manager and see if you have 
 gstreamer good , bad , ugly , and .010 for the linux/ubuntu you use

 everyone get some of these

 gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
 gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
 gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
 gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
 gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

---

### Post by someitalian123 on 2011-06-12
Thanks for the reply. I already deleted ubuntu off the pc because I just think windows would be easier for my dad. Also I was getting alot of lag playing back streaming videos from sites like youtube, I didn't have that problem with windows so I just decided to get rid of it.

---

