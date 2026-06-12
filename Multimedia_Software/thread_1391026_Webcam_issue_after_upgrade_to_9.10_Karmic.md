---
title: "Webcam issue after upgrade to 9.10 Karmic"
date: 2010-01-26
forum: Multimedia Software
---

### Post by aarteaga on 2010-01-26
Hi, recently upgraded to Karmic but after that my webcam stopped working. Mine is a Logitech Quickcam Fusion, working great in windows, ubuntu 8.10 y ubuntu 9.04.

I already reinstalled subversion package and yesterday it worked great, but today when I restarted, the webcam is out again.

Thanks in advance for your help...

$ ls /dev/video
ls: cannot access /dev/video: No such file or directory

$ lsmod|grep video
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
video                  19380  0 
output                  2780  1 video

$ dmesg|grep video
[    0.828925] pci 0000:01:00.0: Boot video device
[   21.091507] Linux video capture interface: v2.00
[   21.094409] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[   22.092158] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   23.092165] uvcvideo: Failed to query (129) UVC probe control : -110 (exp. 26).
[   23.092171] uvcvideo: Failed to initialize the device (-5).
[   23.092234] usbcore: registered new interface driver uvcvideo

---

### Post by RFBrownPE on 2010-03-13
I can find no reply to this question.  Is there a response?

I have exactly the same issue - including the same message:

uvcvideo: Failed to initialize the device (-5).


Any assistance will be greatly appreciated.
Thank you
Bob

---

### Post by cblp on 2010-03-14
Something like this. But I have a new camera and 9.10 and don't know how it works with previous releases.

```
**$ lsmod | grep video**
uvcvideo               59080  0
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
``````
**$ lsusb**
Bus 001 Device 045: ID 18ec:3299 *# NO DESCRIPTION?????????*
...
``````
**$ dmesg | grep video**
[1243900.383153] uvcvideo: Found UVC 1.00 device USB2.0 PC CAMERA (18ec:3299)
[1243900.384980] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[1301088.736770] uvcvideo: Failed to submit URB 0 (-28).

```[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices) says that [18ec:3299] ArkMicro iUSB 2.0 PC Camera (model number QC3231) is fully supported.

[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC) doesn't have any recommendations for 9.10.

Should I try install uvcvideo from hg repo?

---

### Post by no2498 on 2010-03-14
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to, x window system (no xv)
try v4l1 and v4l2 click the bottom test button for each 1
if you are using cheese for the cam and it breaks again you need to do this again

wxcam should work for you just do not open cheese !
cheese is how we set the color now days
and this gstreamer-properties come from the cheese help files
you can get wxcam in a deb file
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by Berduchwal on 2010-03-29
This does not work for me.
Output Plugin: No Xv
Input Plugin: v4l2
results in:
```
libv4l2: error turning on stream: No space left on device
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1886): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src3:
system error: No space left on device]

```
Output Plugin: No Xv
Input Plugin: v4l
```
 gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline4/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Invalid argument]

```
Output Plugin: X Windows
Input Plugin: v4l
```
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline5/GstV4lSrc:v4lsrc3:
Error setting the channel/norm settings: Invalid argument]
```
Output Plugin: X Windows
Input Plugin: v4l2
```
libv4l2: error turning on stream: No space left on device
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1886): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline6/GstV4l2Src:v4l2src5:
system error: No space left on device]

```

I use 9.10 64bit

---

### Post by no2498 on 2010-03-31
i have seen a file you need but its been 6 months or longer

looks some thing like, v41 to v4l2 so

seen it in 1 of the skype help here

sorry just cant think of what 1 it was

did you try the cam in cheese or ekiga softphone

what you did in the gstreamer-properties was set the /dev/video0

you may need to set the pic size in cheese to a smaller size

---

