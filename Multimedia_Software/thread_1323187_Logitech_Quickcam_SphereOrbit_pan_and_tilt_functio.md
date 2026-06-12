---
title: "Logitech Quickcam Sphere/Orbit pan and tilt functionality?"
date: 2009-11-11
forum: Multimedia Software
---

### Post by potatan on 2009-11-11
Hi,

I have a Logitech Quickcam Sphere/Orbit/MP webcam that works fine under Cheese, Camorama, Skype and aMSN.  The camera has functionality for panning and tilting (and I think, Zooming).  It's not a software function, it is actually stepper motors that pan and tilt the lens.  I think the Zooming is virtual though I can't be sure as it's a long time since I attached the camera to a Windows machine to check it out.

So... is there an application that supports pan/tilt for this camera?  Or maybe a set of controls that allow it to pan/tilt whilst in a skype conversation etc.?

I've searched for this functionality and it seems to be supported in a driver (UVC ?) via some libraries, but I can't find an application that includes buttons to pan/tilt the camera.

Any ideas?

(Ubuntu 9.10)

Thanks as always in advance.

---

### Post by fargle on 2009-11-11
I have one as well - it's been awhile, but last time I used it, I believe that using [[COLOR="Blue"]setpwc[/COLOR]]("http://www.vanheusden.com/setpwc/") from the command line allows pan/tilt to work.

---

### Post by potatan on 2009-11-12
cool - setpwc allows me to pan, though the tilt doesn't seem to work (setpwc -x 1000).

But when I try and use it while the cam is in use by another application I get a "device or resource busy" message.

---

### Post by bpickel on 2009-11-12
I finally found a thread the sent me to the fix. I have ALL controls for my Orbit MP 

[http://ubuntuforums.org/showthread.php?t=1286852](http://ubuntuforums.org/showthread.php?t=1286852)

 Most important stuff on this page. 

[http://guvcview.berlios.de/index.html](http://guvcview.berlios.de/index.html)

Using  GTK + UVC

Got to the guvciew page above and follow the instructions there. If you get stuck post back here. Hope this helps !!!

---

### Post by potatan on 2009-11-12
Thanks for the links, looks a good solution...but it didn't work I'm afraid.

When I launch guvcview I get an error dialog:
```
Guvcview error:

Unable to start with minimum setup

Please reconnect your camera
```

Console output:
```

abc@xyz:~$ guvcview 
guvcview 1.1.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. Logitech QuickCam Orbit (location: usb-0000:00:10.4-1.4)
{ pixelformat = 'PWC2', description = 'Raw Philips Webcam' }
   { not supported - request format(843274064) support at http://guvcview.berlios.de }
{ pixelformat = 'YU12', description = '4:2:0, planar, Y-Cb-Cr' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/5, 1/10, 1/15, 
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video0 
/dev/video0 - device 1
Init. Logitech QuickCam Orbit (location: usb-0000:00:10.4-1.4)
{ pixelformat = 'PWC2', description = 'Raw Philips Webcam' }
   { not supported - request format(843274064) support at http://guvcview.berlios.de }
{ pixelformat = 'YU12', description = '4:2:0, planar, Y-Cb-Cr' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/5, 1/10, 1/15, 
checking format: 842093913
Requested Format unavailable: get width 160 height 480 
Unable to set 5 fps
VIDIOC_S_PARM error: Invalid argument
VIDIOC_QUERYBUF - Unable to query buffer: Invalid argument
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...
Terminated.
abc@xyz:~$ 
```

any ideas?

thanks again

---

### Post by potatan on 2009-11-12
A little more - once I have tried running guvcview, both camorama or cheese are unable to detect the camera until I've rebooted.  Disconnecting and reconnecting the USB cable doesn't appear to help either.

---

### Post by bpickel on 2009-11-12
Did you install lbwebcam ?


Also I noted that I need to run guvcview with gksudo.   Once you have done that it doesn't need to be launch administratively.

---

### Post by potatan on 2009-11-13
Hi,

Yes - I have installed libwebcam by following the instructions here:

[http://snipplr.com/view/19847/install-libwebcam-ubuntu-910/](http://snipplr.com/view/19847/install-libwebcam-ubuntu-910/)

The output from the final command there was:
```
xyz@abc:~$uvcdynctrl -c
[libwebcam] Unknown V4L2 user control ID encountered: 0x0098090E (V4L2_CID_USER_BASE + 14)
[libwebcam] Unknown V4L2 user control ID encountered: 0x0098090F (V4L2_CID_USER_BASE + 15)
[libwebcam] Unknown V4L2 user control ID encountered: 0x00980912 (V4L2_CID_USER_BASE + 18)
[libwebcam] Warning: Unsupported V4L2 control type encountered: ctrl_id = 0x08000000, name = 'Save User Settings', type = 4
[libwebcam] Invalid or unsupported custom V4L2 control encountered: ctrl_id = 0x08000000, name = 'Save User Settings'
[libwebcam] Warning: Unsupported V4L2 control type encountered: ctrl_id = 0x08000001, name = 'Restore User Settings', type = 4
[libwebcam] Invalid or unsupported custom V4L2 control encountered: ctrl_id = 0x08000001, name = 'Restore User Settings'
[libwebcam] Warning: Unsupported V4L2 control type encountered: ctrl_id = 0x08000002, name = 'Restore Factory Settings', type = 4
[libwebcam] Invalid or unsupported custom V4L2 control encountered: ctrl_id = 0x08000002, name = 'Restore Factory Settings'
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000003 (V4L2_CID_PRIVATE_BASE + 3)
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000004 (V4L2_CID_PRIVATE_BASE + 4)
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000005 (V4L2_CID_PRIVATE_BASE + 5)
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000006 (V4L2_CID_PRIVATE_BASE + 6)
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000007 (V4L2_CID_PRIVATE_BASE + 7)
[libwebcam] Unknown V4L2 private control ID encountered: 0x08000008 (V4L2_CID_PRIVATE_BASE + 8)
Listing available controls for device video0:
  Noise reduction
  Flickerless
  Backlight compensation
  Contour
  Auto contour
  Colour mode
  Gain Level
  Auto Gain Enabled
  Shutter Speed (Exposure)
  Gamma
  Blue Gain
  Red Gain
  Auto White Balance
  Saturation
  Contrast
  Brightness
xyz@abc:~$ 

```

Running guvcview with gksudo (and with sudo) didn't seem to make a difference - I received the same error dialog.

---

### Post by bpickel on 2009-11-13
Ahh yes ! I remember fist fighting with this a little. Did your make and install go correctly ? 

Here is a post with a little more detail on libwebcam

[http://ubuntuforums.org/archive/index.php/t-1093987.html](http://ubuntuforums.org/archive/index.php/t-1093987.html)

---

### Post by potatan on 2009-11-13
Yes, the compile worked okay but I had to install "cmake" at step 10. Other than that no problems, apart from the output from the final test command.

Okay, I'll give those other instructions a go.

Cheers

---

### Post by potatan on 2009-11-13
Nope - still no good, despite following the latest set of instructions.

I'm beginning to think it may be a Karmic issue, a lot of people seem to have managed to get it working before 28/10/2009... but maybe not so many after perhaps.

thanks for your help up to now.

---

### Post by angelus1969 on 2010-02-13
Any luck with this? I'm getting the same errors with my Orbit/Sphere and can't seem to find a solution anywhere.

---

### Post by zarthon on 2010-02-28
I have one of these too but have not tried to pan and tilt under Linux.
I may try. If it does not work I wonder... how complex the code is, and how hard the bug is to fix? 
Write a clever GUI and Internet remote that works would be clever. What functionality does the software have that must be built and installed outside of the packages manger?

Has anyone gotten this usb ID to work with the existing software on 9.10?

```
lsusb output exerpt:
ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF
```

---

### Post by carignan.boy on 2010-03-11
setpwc -h will display the help for setpwc.

-y x	set pan position
-z x	set tilt position

You need to use -z, not -x to set tilt.

---

### Post by nsk7even on 2011-09-30
setpwc is working for me, but no pan/tilt controls via guvcview. This means I have to stop guvcview (or any other app that is accessing the cam), adjust its orientation with setpwc and restart guvcview.

This is on Ubuntu Natty, kernel 2.6.38-11-generic and all updates.

Did someone got the controls working in natty from within guvcview?

---

### Post by onesojourner on 2013-04-09
> **carignan.boy said:**
> setpwc -h will display the help for setpwc.

-y x	set pan position
-z x	set tilt position

You need to use -z, not -x to set tilt.

That is the info I needed. Thanks a bunch.

---

### Post by wildmanne39 on 2013-04-09
Thread closed. Please do not post in old threads.

---

