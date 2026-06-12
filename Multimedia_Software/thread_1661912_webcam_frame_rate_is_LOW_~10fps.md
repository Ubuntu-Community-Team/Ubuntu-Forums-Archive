---
title: "webcam frame rate is LOW ~10fps"
date: 2011-01-07
forum: Multimedia Software
---

### Post by sdowney717 on 2011-01-07
any way that will improve?
it is a lifecam vx-6000

---

### Post by mikewhatever on 2011-01-07
Lowering the capture resolution might do the trick.

---

### Post by sdowney717 on 2011-01-07
running guvcview shows some settings
the screen says framerate 1/1fps
what does that mean??

```
scott@scott-desktop:~$ guvcview -d /dev/video1
guvcview 1.4.1
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
unexpected integer value (0) for vid_mux
Strings must be quoted
unexpected integer value (1) for snd_numsec
Strings must be quoted
unexpected integer value (160) for snd_bitrate
Strings must be quoted
unexpected integer value (2) for Pan_Step
Strings must be quoted
unexpected integer value (2) for Tilt_Step
Strings must be quoted
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video1 
/dev/video0 - device 1
couldn't open idVendor: /sys/class/video4linux/video0/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video0/../../../idProduct
/dev/video32 - device 2
couldn't open idVendor: /sys/class/video4linux/video32/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video32/../../../idProduct
/dev/video24 - device 3
couldn't open idVendor: /sys/class/video4linux/video24/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video24/../../../idProduct
/dev/video1 - device 4
Init. USB20 Camera     (location: usb-0000:00:1d.7-4)
{ pixelformat = 'BA81', description = 'BA81' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'S920', description = 'S920' }
   { not supported - request format(808597843) support at http://guvcview.berlios.de }
{ pixelformat = 'JPEG', description = 'JPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
vid:045e 
pid:00f4 
driver:sn9c20x
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video1 
/dev/video0 - device 1
couldn't open idVendor: /sys/class/video4linux/video0/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video0/../../../idProduct
/dev/video32 - device 2
couldn't open idVendor: /sys/class/video4linux/video32/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video32/../../../idProduct
/dev/video24 - device 3
couldn't open idVendor: /sys/class/video4linux/video24/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video24/../../../idProduct
/dev/video1 - device 4
Init. USB20 Camera     (location: usb-0000:00:1d.7-4)
{ pixelformat = 'BA81', description = 'BA81' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'S920', description = 'S920' }
   { not supported - request format(808597843) support at http://guvcview.berlios.de }
{ pixelformat = 'JPEG', description = 'JPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
vid:045e 
pid:00f4 
driver:sn9c20x
checking format: 825770306
Requested Format unavailable: get width 160 height 120 
fps is set to 0/0
drawing controls

VIDIOC_G_EXT_CTRLS failed
   using VIDIOC_G_CTRL for user class controls
fps is set to 1/1
setting new resolution (640 x 480)
checking format: 825770306
setting new resolution (640 x 480)
checking format: 1195724874
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
setting new resolution (640 x 480)
checking format: 861030210
setting new resolution (640 x 480)
checking format: 825770306
setting new resolution (640 x 480)
checking format: 1195724874
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
Audio frame size is 1152 samples for selected codec
Stoping audio stream
Closing audio stream...
write /home/scott/.guvcviewrc-video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK
scott@scott-desktop:~$ guvcview -d /dev/video1
guvcview 1.4.1
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video1 
/dev/video0 - device 1
couldn't open idVendor: /sys/class/video4linux/video0/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video0/../../../idProduct
/dev/video32 - device 2
couldn't open idVendor: /sys/class/video4linux/video32/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video32/../../../idProduct
/dev/video24 - device 3
couldn't open idVendor: /sys/class/video4linux/video24/../../../idVendor
couldn't open idProduct: /sys/class/video4linux/video24/../../../idProduct
/dev/video1 - device 4
Init. USB20 Camera     (location: usb-0000:00:1d.7-4)
{ pixelformat = 'BA81', description = 'BA81' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'S920', description = 'S920' }
   { not supported - request format(808597843) support at http://guvcview.berlios.de }
{ pixelformat = 'JPEG', description = 'JPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 
vid:045e 
pid:00f4 
driver:sn9c20x
checking format: 1195724874
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 0/0
drawing controls

VIDIOC_G_EXT_CTRLS failed
   using VIDIOC_G_CTRL for user class controls
fps is set to 1/1


```

---

### Post by sdowney717 on 2011-01-07
tried dropping to lower resolutions with cheese and makes no difference.

the 1/1 fps is listed and I cant open that setting.
does this mean 1 FPS?

---

### Post by sdowney717 on 2011-01-07
guvcview says the frame rate is 3.5fps
pretty slow!

---

### Post by sdowney717 on 2011-01-07
well i sort of figured out why it is so low.
I pointed the camera to an outside light source, and the frame rate went to 30

I wonder if the vfl2 setting of 'auto exposure' would make a diff as i read some  suggested to uncheck it, but noticed no diff for me.

---

### Post by sdowney717 on 2011-01-07
turned on some more lights

using guvcview, nice program I adjusted some things.

left auto exposure on
turned gain upto 18
and getting decent picture at 28fps
so I will mark it solved

---

### Post by sdowney717 on 2011-01-07
turned on some more lights

using guvcview, nice program I adjusted some things.

left auto exposure on
turned gain upto 18
and getting decent picture at 28fps
so I will mark it solved

---

