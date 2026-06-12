---
title: "Logitech C9000 not working with USB 3.0"
date: 2010-12-23
forum: Multimedia Software
---

### Post by cityguru on 2010-12-23
I have in my computer a USB 3.0 controller going through my PCI-E slot. I then connected a 3.0 USB HUB.  When i try to access Cheese or any other webcam program I get the following error.

I am trying to run multiple webcams and apparently there is a trick where you can use a USB 3.0 controller and USB 3.0 hub and then connect regular USB 2.0 webcams to it.  On my windows enviroment i tried this out and i was able to run 10 webcams at once.

On Ubuntu it definitely recognizes the USB 3.0 controller as well as hub when i do a lsusb command.  It also recognizes in lsusb the Logitech camera.  But when i try to initiate Cheese or guvcview it opens the interface and it looks like it tries to access the camera since i see a window pop up but then very quickly disappears.

I also tried running another program which accesses a video feed and i get the following error

 system error: starting video stream (VIDIOC_STREAMON): Invalid argument (22).


I tried it also removing the USB 3.0 hun as well.  Like i said lsusb shows me it recognizes all the equipment, its just that no program seems to be able to show the video.


Any help would be very much appreciated

---

### Post by no2498 on 2010-12-23
only try 1 cam at a time
if i plug in 2 cam's and try 1 at a time the system gets confused 
hub's was a no no with usb 2.0 so not sure of 3.0

try the cam in vlc media player
click media, click open capture divice, play

cheese may not be up to par with 3.0 yet


as for 2 or more cams at a time
you need a security program for linux/ubuntu

---

### Post by cityguru on 2010-12-23
I did try one camera at a time with and without the hub. Also tried gucview even in command line. Its definitey not aout the software its something to do with he driver and uvc linux or something like that.

---

### Post by no2498 on 2010-12-24
you try this yet

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

you may need to change the plugin at times

---

### Post by cityguru on 2010-12-24
I am definitely going to try this, i have actually been pondering if somehow the 3.0 controller some how forces the wrong driver or something.  Keep in mind on 2.0 controller in the same computer everything works fine, just when connected to the 3.0 controller with or without the hub i get this error.

Ill try and force those drivers as you mentioned and keep you posted, thanks for the suggestion.

---

### Post by jonim8or on 2011-01-07
Did you get it to work? I'm asking because I'm trying to connect two C910's to my laptop.

---

### Post by evilxsystems on 2011-01-11
I'm having the same problem with usb2.0 logitech cameras on my usb 3.0 card.  All of the cameras work fine when plugged into my usb2.0 ports but none work when I run them off the usb3.0 card, they are listed as /dev/video0../dev/videoN but when I try to use them using guvcview or streamer I get the following errors:

```
medusa@medusa-OptiPlex-780:~$ guvcview -d /dev/video0
guvcview 1.4.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
/dev/video0 - device 1
/dev/video1 - device 2
/dev/video2 - device 3
/dev/video3 - device 4
/dev/video4 - device 5
/dev/video5 - device 6
Init. UVC Camera (046d:09c2) (location: usb-0000:03:00.0-3.1)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
vid:046d 
pid:09c2 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Operation not permitted
checking format: 1196444237
libv4l2: error setting pixformat: Device or resource busy
VIDIOC_S_FORMAT - Unable to set format: Device or resource busy
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video0 
/dev/video0 - device 1
/dev/video1 - device 2
/dev/video2 - device 3
/dev/video3 - device 4
/dev/video4 - device 5
/dev/video5 - device 6
Init. UVC Camera (046d:09c2) (location: usb-0000:03:00.0-3.1)
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
    Time interval between frame: 2/15, 1/5, 
vid:046d 
pid:09c2 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Operation not permitted
checking format: 1196444237
libv4l2: error setting pixformat: Device or resource busy
VIDIOC_S_FORMAT - Unable to set format: Device or resource busy
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

```
medusa@medusa-OptiPlex-780:~$ streamer -t 17:0:0 -s 640x480 -r .4167 -c /dev/video0 -o ./bigger000000.pgm
files / video: 8 bit StaticGray / audio: none
libv4l2: error setting pixformat: Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=640;fmt.pix.height=480;fmt.pix.pixelformat=0x56595559 [YUYV];fmt.pix.field=NONE;fmt.pix.bytesperline=1280;fmt.pix.sizeimage=614400;fmt.pix.colorspace=SRGB;fmt.pix.priv=0): Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=640;fmt.pix.height=480;fmt.pix.pixelformat=0x56595559 [YUYV];fmt.pix.field=NONE;fmt.pix.bytesperline=1280;fmt.pix.sizeimage=614400;fmt.pix.colorspace=SRGB;fmt.pix.priv=0): Device or resource busy
no way to get: 640x480 8 bit StaticGray
movie writer initialisation failed
medusa@medusa-OptiPlex-780:~$ 

```



When I run gstreamer-properties I can test the cameras plugged into the usb2.0 ports but the same cameras plugged into usb3.0 gives: 

```

medusa@medusa-OptiPlex-780:/dev$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1280x960 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YUYV @ 1280x960: Device or resource busy]
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1280x960 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline5/GstV4l2Src:v4l2src2:
Call to S_FMT failed for YUYV @ 1280x960: Device or resource busy]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline6/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1280x960 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline7/GstV4l2Src:v4l2src3:
Call to S_FMT failed for YUYV @ 1280x960: Device or resource busy]
libv4l2: error setting pixformat: Device or resource busy
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1280x960 [gstv4l2object.c(1951): gst_v4l2_object_set_format (): /GstPipeline:pipeline10/GstV4l2Src:v4l2src6:
Call to S_FMT failed for YUYV @ 1280x960: Device or resource busy]
libv4l2: error turning on stream: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline11/GstV4l2Src:v4l2src7:
system error: Invalid argument]
libv4l2: error turning on stream: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video2'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline12/GstV4l2Src:v4l2src8:
system error: Invalid argument]
libv4l2: error turning on stream: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video3'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline13/GstV4l2Src:v4l2src9:
system error: Invalid argument]
```

---

### Post by no2498 on 2011-01-12
to use more than 1 cam at a time you need a program for it

linux security cam programs

---

### Post by evilxsystems on 2011-01-12
that is not true.  I upgraded to the 2.6.36 kernel and now have 4 cameras recording....two on the usb 2.0 bus on the motherboard and two on the usb 3.0 card....I'm going to try to install another card to bring it up to six cameras...will report back if it works

---

### Post by no2498 on 2011-01-12
? usb cards

---

### Post by evilxsystems on 2011-01-12
PCIe usb card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815158181](http://www.newegg.com/Product/Product.aspx?Item=N82E16815158181)

---

### Post by evilxsystems on 2011-01-12
also I can visualise six cameras using guvcview on the 2.0 bus, but can only record 2 cameras

---

