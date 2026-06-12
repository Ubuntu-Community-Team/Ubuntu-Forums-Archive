---
title: "Can't get Logitech webcam to work"
date: 2010-12-31
forum: Multimedia Software
---

### Post by PDA1 on 2010-12-31
I'm trying to get my Logitech webcam to work.  I don't know the exact model but it's a round globe.

Lsusb says- 

Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate


I've tried Cheese, VLS but no video as of yet.

Any ideas how to fix it?

---

### Post by no2498 on 2010-12-31
put this in google
ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate


you may try to see if it comes on this way first

click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

---

### Post by PDA1 on 2010-12-31
Can't find anything called-- System, Preferences------->multimedia systems selector.

---

### Post by no2498 on 2010-12-31
very top of your screen
applications, places, system

---

### Post by PDA1 on 2010-12-31
I understood where you were directing me but there is no multimedia systems selector in Preferences.

---

### Post by no2498 on 2011-01-02
odd its 16 down from the top on/in 10.04 lucid


open a terminal type gstreamer-properties click enter
click video try v4l and v4l2
click the bottom test for each 1

---

### Post by PDA1 on 2011-01-03
Here are the results.....


```
desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src1:
system error: Input/output error]
```


.....Any ideas?

---

### Post by no2498 on 2011-01-03
see if changing the plugins help in gstreamer-properties


did you look to see if you needed a driver
i think you do
i am thinking you need to use uvc and i have see a few that need to do some thing like a modprob of it

---

### Post by PDA1 on 2011-01-03
Changing the plugins had no effect.

What's UVC and modprob?

---

### Post by no2498 on 2011-01-03
[http://www.google.com/search?client=opera&rls=en&q=ID+046d:08f5+Logitech,+Inc.+QuickCam+Messenger+Communicate&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=ID+046d:08f5+Logitech,+Inc.+QuickCam+Messenger+Communicate&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)




Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. QuickCam Messenger Communicate

---

### Post by PDA1 on 2011-01-03
Could you please explain your ideas?  I have no idea what you're telling me.  I looked at the endless google link about the web cam but can make no sense of the what techno-geeks are talking about.

---

### Post by no2498 on 2011-01-04
just slow down some thing will pop up and you will see if it may help you
go back and read some more

---

### Post by PDA1 on 2011-01-04
Anybody else know how to fix this thing?

---

