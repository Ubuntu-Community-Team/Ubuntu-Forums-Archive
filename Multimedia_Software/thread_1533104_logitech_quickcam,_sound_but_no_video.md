---
title: "logitech quickcam, sound but no video"
date: 2010-07-17
forum: Multimedia Software
---

### Post by Anoobis on 2010-07-17
Bit of a newbie here by the way.
ubuntu 10.4 on an acer revo,

Using a logitech quickcam messenger and wanting to video call on skype.
The test call (sound only) works fine and i can hear myself using the microphone on the camera. can also record myself in "sound recorder" that comes with ubuntu

Things I have done:
In the skype video settings there is an option for camera (/dev/video0) but clicking the test gives nothing.

Looking at the video4linux control panel it reads:
Driver         STV06xx
card           camera
bus_info       usb-0000:00:04.0-6
version        2.7.0
capabilities   0x05000001
Starting the preview just gives a green screen.

lsusb in terminal window gives:
```
Bus 002 Device 006: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
```

Camorama gives an error - "unable to capture image"

Trying to record direct from webcam on youtube worked at one point but was zoomed in (despite not having physical zoom function on camera?), very pixelated. At this point in the skype video settings it certainly said something other than "camera (/dev/video0)" but when I tried to test, it just shut down skype.
Thought I was halfway there. logged off ubuntu but back on youtube says "no camera was found" and skype still has "camera (/dev/video0)"

related note - video playback (files, youtube etc) is v slow was going to make seperate thread about it after getting nowhere. not sure if this will be related in the whole video4linux?

---

### Post by no2498 on 2010-07-18
have you tried the cam in cheese webcam booth 


and for skype try this open a terminal put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


hope that helps

---

### Post by Anoobis on 2010-07-23
cheese webcam booth doesn't show anything either and when i run

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
then go into skype options, click the webcam test screen the terminal window reads:
libv4l2: error turning on stream: Input/output error

Anyone else have any ideas?

---

### Post by no2498 on 2010-07-23
this is how ubuntu/linux test webcams

but it sounds like your not getting the pipe setup




open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope it helps

---

