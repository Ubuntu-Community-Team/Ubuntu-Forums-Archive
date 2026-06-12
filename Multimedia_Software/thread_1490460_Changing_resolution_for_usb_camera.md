---
title: "Changing resolution for usb camera"
date: 2010-05-22
forum: Multimedia Software
---

### Post by rdbowers on 2010-05-22
I've been having a fit with Ubuntu (even tried updating to the new version).  I have a USB camera (1.3mp- 1024x768 ) that I need to observe and capture images with (microphotography).  I've downloaded and installed multiple packages, but have not found any way to change the default resolutions for V4l2.  The resolution closest to what I need is 1024x816, but the video is torn and unusable.  One program, Kamoso, worked fine in 640x480 mode, but as soon as I upgraded to Ubuntu 10, it went to the higher resolution (1024x816) which doesn't work right.

Is there some way to force v4l2 into a 1024x768 mode?

The camera is a Tucsen 1.3mp microscope camera.  I've emailed the company for more information and to see if they would email me the software/drivers (I lost the driver disk in a fire), but nothing so far from them.

The programs I've installed and tried: Camorama, Kamoso, Xsane, Cheese, VLC media player, v4l2ctrl, v4l2ucp, v4lctl, v4l-info.  Camorama doesn't work, Kamoso- you couldn't change resolutions (ditto for Xsane), Cheese - I can change resolutions, but they have these crazy values that don't work, VLC media I cannot change either.

I'm supposed to be able to use v4l2ucp to change settings, but I don't get the screen that the preview for the program (in Ubuntu Software) showed.

---

### Post by rdbowers on 2010-05-27
Further information:  the usb camera is based upon an Empia technology 2750 webcam.  I still am unable to get this to work right with Linux, although it is supposed to.  The video is distorted whenever you try to go above 640x480.  Below that, it works fine.  I still cannot figure out how to force the resolution to normal values- i.e. 1024x768 (the highest resolution by the camera) instead of 1024x816 (which the camera doesn't support).

(Added information):

results of lsusb: Bus 001 Device 008: ID eb1a:2750 eMPIA Technology, Inc. ECS Elitegroup  G220 integrated Webcam

Trying to run luvcview- it crashes with the report "Init V4L2 failed!! exit fatal".

---

### Post by tgalati4 on 2010-05-28
It's possible that the higher resolution is for still images only.  Normally usb video cameras have 1/2 to 1/4 the resolution when used in video mode (15 to 30 frames per second).  So, for example if you want 15 fps video you may only get 1/2 resolution and 30 fps you might only get 1/4 resolution.

Were you able to record video in full 1024x768 in Windows?

---

### Post by rdbowers on 2010-05-28
I can use it fully in Windows, although I do not use it for video- it will display 1024x768 in preview mode without any problem.  The framerate might be a bit slow for video (20fps, I think) but not a problem for what I use it for.

The problem seems to be some sort of setup in the driver.  I don't know how to make changes or if this might be some sort of bug.

---

### Post by no2498 on 2010-05-28
as of 910 and up my under standing is
ubuntu give all the webcam settings to cheese :(

hope you find a way to fix it

---

### Post by rdbowers on 2010-05-28
That's the way it looks.  It seems to me that the driver has had these resolutions embedded in them, and they're "locked in rock".  I was hoping that there would be something that could be adjusted somewhere, but no luck finding it.

I tried emailing the manufacturers (in China), but like usual with companies from China, they don't respond (unless you're going to buy something).

---

### Post by tgalati4 on 2010-05-28
My understanding is to use multiples of 16 for resolution modes in v4l2.  Technically you can use any resolution, but because of software encoding, it's quicker using 16x multiples for horizontal and vertical resolution.

Also, the kernel needs to know if a device hogs memory.

Add this to the bottom of /etc/sysctl.conf then reboot:

# Added 28 May 2010 to support higher res cameras on zoneminder
kernel.shmall = 134217728
kernel.shmmax = 134217728

---

