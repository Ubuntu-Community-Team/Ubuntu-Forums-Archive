---
title: "Cheese, anyone?"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Roger D on 2008-05-21
Hi

I'm running Hardy, via a fresh install, on a  PC with an Athlon 64 3000 processor. My webcam is a Logitech Quickcam Pro 9000, carefully chosen because it uses the uvc drivers, part of Hardy.

The webcam, along with its built-in mic, are recognised by my PC.

roger@roger-desktop-new:~$ lsusb
Bus 002 Device 006: ID 045e:009d Microsoft Corp. 
Bus 002 Device 005: ID 03f0:7204 Hewlett-Packard DeskJet 36xx
Bus 002 Device 004: ID 058f:6254 Alcor Micro Corp. 
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 002 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
roger@roger-desktop-new:~$ 

roger@roger-desktop-new:~$ sudo cat /proc/asound/pcm
01-00: USB Audio : USB Audio : capture 1
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
roger@roger-desktop-new:~$ 

So, looking pretty good. Also, the video test in Skype works - the activity light on my webcam lights up, and I get a small, but clear image in the Skype window.

When it comes to using Cheese, however, things are not so good. I select Cheese, the Cheese window opens and the webcam activity light comes on. Then, after a few seconds, the light goes off, leaving the Cheese window blank. All I can do is close down the Cheese window.

I've found a way of getting Cheese to do a bit more - it involes starting cheese, and then, just after the activity light goes off, clicking one one of the Cheese menu button, e.g. Help. This makes the light come on again, and I get an image in the Cheese window. It's a nice clear sharp image, the only problem is there's a time delay of around one second before the screen image responds to events in the real world.

Looking at the Cheese FAQs, I can see that this is a common problem. Here's the advice:

You may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.

Using gstreamer-properties I've managed to do that.

The Plugin on my default video output is now 'X Window System (X11/XShm/Xv)', and on my Default input the plug in is 'Video for Linux 2 (v4|2) and the device is 'UVC Camera (046d:0990), which, as far as I can tell is all as it should be. However, this doesn't solve the slow video response with Cheese, and, when I click on test for the video default input, I sometimes get the message: Video for Linux 2 (v4|2): Device '/dev/video' cannot capture at 1600x1200, and sometimes it sort of works, producing a large, but slow video image. Sorry, but I can't work out why it works on some occasions, and not others. Here's my terminal output when it doesn't work:

roger@roger-desktop-new:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1194): gst_v4l2src_set_capture (): /pipeline0/v4l2src3:
Call to S_FMT failed for YUYV @ 1600x1200: Device or resource busy]


Anybody got any ideas what could be wrong? I thought the problem might be down to the limitations of my CPU, but the camera works fine on my XP box

Roger D

---

### Post by Roger D on 2008-05-25
Hi

I've given up of Cheese - this seems of be a fairly common problem, with no known solution. However, I'm now successfully recording vidoe, complete with sound, using gvucview. If Cheese isn't working for you either, it's well worth a try:

[http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

Roger D

---

### Post by freackout on 2009-06-25
> **Roger D said:**
> Hi

I'm running Hardy, via a fresh install, on a  PC with an Athlon 64 3000 processor. My webcam is a Logitech Quickcam Pro 9000, carefully chosen because it uses the uvc drivers, part of Hardy.

The webcam, along with its built-in mic, are recognised by my PC.

roger@roger-desktop-new:~$ lsusb
Bus 002 Device 006: ID 045e:009d Microsoft Corp. 
Bus 002 Device 005: ID 03f0:7204 Hewlett-Packard DeskJet 36xx
Bus 002 Device 004: ID 058f:6254 Alcor Micro Corp. 
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 002 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
roger@roger-desktop-new:~$ 

roger@roger-desktop-new:~$ sudo cat /proc/asound/pcm
01-00: USB Audio : USB Audio : capture 1
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
roger@roger-desktop-new:~$ 

So, looking pretty good. Also, the video test in Skype works - the activity light on my webcam lights up, and I get a small, but clear image in the Skype window.

When it comes to using Cheese, however, things are not so good. I select Cheese, the Cheese window opens and the webcam activity light comes on. Then, after a few seconds, the light goes off, leaving the Cheese window blank. All I can do is close down the Cheese window.

I've found a way of getting Cheese to do a bit more - it involes starting cheese, and then, just after the activity light goes off, clicking one one of the Cheese menu button, e.g. Help. This makes the light come on again, and I get an image in the Cheese window. It's a nice clear sharp image, the only problem is there's a time delay of around one second before the screen image responds to events in the real world.

Looking at the Cheese FAQs, I can see that this is a common problem. Here's the advice:

You may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.

Using gstreamer-properties I've managed to do that.

The Plugin on my default video output is now 'X Window System (X11/XShm/Xv)', and on my Default input the plug in is 'Video for Linux 2 (v4|2) and the device is 'UVC Camera (046d:0990), which, as far as I can tell is all as it should be. However, this doesn't solve the slow video response with Cheese, and, when I click on test for the video default input, I sometimes get the message: Video for Linux 2 (v4|2): Device '/dev/video' cannot capture at 1600x1200, and sometimes it sort of works, producing a large, but slow video image. Sorry, but I can't work out why it works on some occasions, and not others. Here's my terminal output when it doesn't work:

roger@roger-desktop-new:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1600x1200 [v4l2src_calls.c(1194): gst_v4l2src_set_capture (): /pipeline0/v4l2src3:
Call to S_FMT failed for YUYV @ 1600x1200: Device or resource busy]


Anybody got any ideas what could be wrong? I thought the problem might be down to the limitations of my CPU, but the camera works fine on my XP box

Roger D
i have had cheese working perfectly on a single core machine with differing cameras, however upon installing with a duall/quad core had many problems, my solution was to use guvcview it's better by far the cpu is not hogged + another major tip get a uvc compatible camera good results here plug n play quickcam pro 9000 by logitech i believe the 5000 is also compatible and may be cheaper than £45 ok getting 1600*1200 res recording at ave 120% cpu. on cheese, but only 960*720 res on guvcview averaging out about 25% cpu odd gutter (hardly) but better control of setting on the overall programme, tonnes of settings to play with..no probs both programmes installed here mint 6 gloria (intrepid)...lovely happy at last UVC Camera saves loads of hassle too installing modules ect.

---

### Post by freackout on 2009-06-25
> **freackout said:**
> i have had cheese working perfectly on a single core machine with differing cameras, however upon installing with a duall/quad core had many problems, my solution was to use guvcview it's better by far the cpu is not hogged + another major tip get a uvc compatible camera good results here plug n play quickcam pro 9000 by logitech i believe the 5000 is also compatible and may be cheaper than £45 ok getting 1600*1200 res recording at ave 120% cpu. on cheese, but only 960*720 res on guvcview averaging out about 25% cpu odd gutter (hardly) but better control of setting on the overall programme, tonnes of settings to play with..no probs both programmes installed here mint 6 gloria (intrepid)...lovely happy at last UVC Camera saves loads of hassle too installing modules ect.

sorry i have amd x4 cpu. i meant total 120% cpu then average 25%.

---

### Post by freackout on 2009-06-25
> **freackout said:**
> sorry i have amd x4 cpu. i meant total 120% cpu then average 25%.

gitter not gutter

---

### Post by freackout on 2009-06-25
> **freackout said:**
> gitter not gutter

in guvcview i find bringing the res down to say 800x600 improves things dramatcally ie now at 5% cpu which is just dandy for me.....ok guys.

---

