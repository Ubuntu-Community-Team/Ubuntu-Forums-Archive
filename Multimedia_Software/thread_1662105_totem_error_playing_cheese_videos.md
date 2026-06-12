---
title: "totem error playing cheese videos"
date: 2011-01-07
forum: Multimedia Software
---

### Post by sdowney717 on 2011-01-07
getting an error after recording video from webcam with cheese.
totem cant play these ogv files, BUT VLC can play them
thoughts?
I run cheese from terminal to expose the issue.

> ** (cheese:22639): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-124826.ogv (video/ogg)

scott@scott-desktop:~$ totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.



```
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
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1)
   using VIDIOC_S_CTRL for user class controls
VIDIOC_G_EXT_CTRLS failed
   using VIDIOC_G_CTRL for user class controls
VIDIOC_S_EXT_CTRLS for multiple controls failed (error -1)
   using VIDIOC_S_CTRL for user class controls
VIDIOC_G_EXT_CTRLS failed
   using VIDIOC_G_CTRL for user class controls
write /home/scott/.guvcviewrc-video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK
scott@scott-desktop:~$ cheese
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.

(cheese:15460): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105936.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104116.ogv'
Reason: Took too much time to process.

** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104116.ogv (video/ogg)


** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105936.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105855.ogv'
Reason: Took too much time to process.

** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105855.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105457.ogv'
Reason: Took too much time to process.

** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105457.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105304.ogv'
Reason: Took too much time to process.

** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105304.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.

** (cheese:15460): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104056.ogv (video/ogg)

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
write /home/scott/.guvcviewrc-video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK
scott@scott-desktop:~$ cheese
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.

(cheese:15765): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105457.ogv'
Reason: Took too much time to process.

** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105457.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105304.ogv'
Reason: Took too much time to process.

** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105304.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105936.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105855.ogv'
Reason: Took too much time to process.

** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105936.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104116.ogv'
Reason: Took too much time to process.

** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105855.ogv (video/ogg)


** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104116.ogv (video/ogg)


** (cheese:15765): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104056.ogv (video/ogg)

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
write /home/scott/.guvcviewrc-video1 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK
scott@scott-desktop:~$ cheese
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.

(cheese:17307): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105457.ogv'
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105855.ogv'
Reason: Took too much time to process.
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104116.ogv'
Reason: Took too much time to process.

** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104116.ogv (video/ogg)


** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105855.ogv (video/ogg)


** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105457.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105304.ogv'
Reason: Took too much time to process.

** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105304.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.

** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104056.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105936.ogv'
Reason: Took too much time to process.

** (cheese:17307): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105936.ogv (video/ogg)

/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
scott@scott-desktop:~$ skype
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
scott@scott-desktop:~$ cheese
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.

(cheese:18017): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104116.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105304.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105457.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105936.ogv'
Reason: Took too much time to process.

** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105304.ogv (video/ogg)


** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104116.ogv (video/ogg)


** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105457.ogv (video/ogg)


** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105936.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.

** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-104056.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105855.ogv'
Reason: Took too much time to process.

** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-105855.ogv (video/ogg)


** (totem-video-thumbnailer:18214): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:18214): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:18214): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:18214): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:18214): WARNING **: Could not take screenshot: no video info
totem-video-thumbnailer couldn't get a picture from 'file:///home/scott/Videos/Webcam/2011-01-07-124826.ogv'

** (cheese:18017): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-124826.ogv (video/ogg)

scott@scott-desktop:~$ cheese
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.

(cheese:22639): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

** (totem-video-thumbnailer:22666): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:22666): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:22666): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:22666): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:22666): WARNING **: Could not take screenshot: no video info
totem-video-thumbnailer couldn't get a picture from 'file:///home/scott/Videos/Webcam/2011-01-07-124826.ogv'

** (cheese:22639): WARNING **: could not generate thumbnail for /home/scott/Videos/Webcam/2011-01-07-124826.ogv (video/ogg)

scott@scott-desktop:~$ totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104056.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105936.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105457.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-104116.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105855.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/scott/Videos/Webcam/2011-01-07-105304.ogv'
Reason: Took too much time to process.
^C
scott@scott-desktop:~$ 

```

---

### Post by gordintoronto on 2011-01-07
How fast is your computer?  VLC installs some of its own codecs, so that might be the issue.

---

### Post by BicyclerBoy on 2011-01-07
VLC & some others are stream players.
They are able to handle streams with errors/bits missing/broken headers..
They do not need perfect complete files to be able to play something.

So VLC is much more robust then totem.

You could run the files thru' VLC or ffmpeg to fix them ..

---

### Post by sdowney717 on 2011-01-08
It is a core2 duo 3.0 ghz intel type chip
4gb ddr2
asus mb

> You could run the files thru' VLC or ffmpeg to fix them ..
any quick command you can share?

---

### Post by no2498 on 2011-01-09
type smplayer in a terminal click enter
it tells you how to install it
that should help totem
or smplayer will play them

---

