---
title: "guvcview video? file documentation"
date: 2016-05-21
forum: Multimedia Software
---

### Post by jgw on 2016-05-21
The camera I am using is a Sony Effio 1/3 CCD 36 IR Leds Outdoor Security CCTV Camera.  The video output is a bnc connector.  I used a female bnc to female rca connector, then an male rca connector to connect to the easycap usb video capture video input.  (I tried the easycap and another, bought on ebay, guaranteed to work with ubuntu).  Anyway, lsusb shows me that I am connected via Bus 004 Device 002: ID eb1a:2890 eMPIA Technology, Inc.  (guvcview and VLC shows UVC camera (eb1a:2890))  guvcview gives me a blank black screen and VLC gives me a blank blue screen.  I have tried all available camera output options ( 'yuyv, yu12, yv12,  rgb3, bgr3, and mjpg(default)) Sometimes the screen is black, or blue, or green but they are all blank.  If I tell guvcview to create a file Its an .mkv file.  The difference in output, between VLC and guvcview is that sometimes the color of the blank output changes, one from the other.  Both programs tell me that the fps is running between 19.5 and 20  

Since there are a lot more video format modes than those I tried (available in guvcview) I wonder if I should force the others, one at a time, in video2 to see if that makes a difference.  Oh, when guvcview creates and writes to a file it puts a title into the first couple of seconds which I can see as its printed over the output(blank screen).  

So, my machine recognizes the usb video capture input.  It also seems to see the camera (/dev/video2)  It just doesn't seem to see any video.  I have connected the camera directly to the tv and the camera works (and actually shows where its looking).  I have also hooked up two different usb webcams just to see if I could.  I could, and they worked just fine.  I am now wondering if this camera is never going to work and I should get myself a weatherproof usb camera instead of the one I bought and gives me blank screens.  

Hopefully somebody can aim me in the right direction to get this working - thank you.............

---

