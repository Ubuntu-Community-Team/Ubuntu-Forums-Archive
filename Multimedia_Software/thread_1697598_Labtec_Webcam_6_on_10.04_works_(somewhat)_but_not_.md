---
title: "Labtec Webcam 6 on 10.04 works (somewhat) but not on 10.10"
date: 2011-03-01
forum: Multimedia Software
---

### Post by dieter-erich on 2011-03-01
Hi,
  By using the preload command D_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype I got my Labtec Webcam 6 to work in cheese and in skpe (although with a number of errors coming up in the terminal - see another post of mine) in ubuntu 10.04. I now updated to ubuntu 10.10 and now I do not get any errors but not any picture either. It just remains black regardless of whether I do the preload or not. 
Any ideas are appreciated!

---

### Post by no2498 on 2011-03-01
open a terminal type gstreamer-properties click enter
click video try v4l and v4l2
use the bottom test button for each 1

this comes from the cheese help FAQ'S


&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by dieter-erich on 2011-03-02
Thanks a lot! 

Regardless of the plugin settings I get, in With v4i2, a black window (as I was having before), and in v4i1 a garbled (much smaller) image and the error message: 

Error running pipeline 'Video for Linux (v4l)': Die Einstellungen konnten nicht aus der Ressource gelesen oder in die Ressource geschrieben werden. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc1:Error setting the channel/norm settings: Das Argument ist ungültig]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Die Einstellungen konnten nicht aus der Ressource gelesen oder in die Ressource geschrieben werden. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline4/GstV4lSrc:v4lsrc2:.......

Which translates into: The settings could neither be read nor wrote from/into the resource
and:
The argument is not valid

I can enter two devices (Radeo Textured Video or ATI Xwindow System - X11/Xshm/Xv) with the first one I get a crash with the second one the test gives me the windows described above,

What does this mean?

---

### Post by no2498 on 2011-03-02
gstreamer needs to have the
good, bad, ugly, and 10 installed
also find and install xawtv
try the cam in xawtv
it loads a cam grabber with it

---

### Post by dieter-erich on 2011-03-03
[B]Installed xawtv, checked with 
gstreamer_properties[/B]
####
nora@nora-laptop:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Die Einstellungen konnten nicht aus der Ressource gelesen oder in die Ressource geschrieben werden. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Das Argument ist ungültig]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Die Einstellungen konnten nicht aus der Ressource gelesen oder in die Ressource geschrieben werden. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline7/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Das Argument ist ungültig]
gstreamer-properties-Message: Error running pipeline 'Custom': Die Einstellungen konnten nicht aus der Ressource gelesen oder in die Ressource geschrieben werden. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline8/GstV4lSrc:v4lsrc3:
Error setting the channel/norm settings: Das Argument ist ungültig]

[B]Only with the settings:_ Xwindow System (no Xv)_ I get the colorful test image with all other settings it is black
Only Video for linux 2 (v4l2) recognizes the Web cam but gives a black screen[/B]

**then tried xawtv:**

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.35-27-generic)
xinerama 0: 1024x768+0+0
xinerama 1: 1024x768+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x1 [PAL_B]): Das Argument ist ungültig
ioctl: VIDIOC_S_STD(std=0x0 []): Das Argument ist ungültig

**I get a black window with a red dot on the left side :-))**

[B]Any suggestions? The point is that I already got further with 10.04 (at least a picture, although a lot of error messages). So what is different in 10.10?
[/B]

---

### Post by dieter-erich on 2011-03-03
Sorry, despite all I wrote before, Cheese is working! Skype still not! In the skype options, although it seems to recognize that there is a camera, it does not show an image. But this might be related to the fact that the PC is quite old and since the upgrade to 10.10 appears to be very slow....
in any case, thanks for the hints!

---

### Post by no2498 on 2011-03-03
glad you got it working some what
you now have something to work with

for the slow computer
open a terminal type in htop click enter 
it tells you how to install it
after installed type htop click enter
see if you can see any thing using to much memory or the cpu
it tells you how to stop things and turn it off/htop
you can find htop in the system tools after its loaded
if you need to use it again

---

### Post by dieter-erich on 2011-03-04
Well, I believe that I had some troubles with skype. I re-installed it and now I have about 5% cpu load. 

However, when testing the video (in skype> options > video) it just shows the black window and apparently video does not work. In cheese it does. So, this is now a problem of skype and not of the video driver anymore. I might post this in a skype forum. Or do you have any suggestions?

---

### Post by no2498 on 2011-03-04
no i do not use skype
i would look in there FAQ'S its had to have been ask before

---

