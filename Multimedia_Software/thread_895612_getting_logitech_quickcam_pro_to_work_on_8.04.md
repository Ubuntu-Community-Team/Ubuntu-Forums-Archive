---
title: "getting logitech quickcam pro to work on 8.04"
date: 2008-08-20
forum: Multimedia Software
---

### Post by untill on 2008-08-20
Webcam, again. :(

I have Logitech QuickCam Pro for Notebooks.

I plug in the USB.

Output from dmesg:
[   25.355782] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)

Output from lsusb:
Bus 007 Device 006: ID 046d:0991 Logitech, Inc.

Listing of video device:
> ls -l /dev/video1 
crw-rw----+ 1 root video 81, 1 2008-08-20 16:53 /dev/video1
> grep video /etc/group
video:x:44:my_user_name

I start ekiga and configure the video with plugin v4l2. The cam works, that is, the light turns on and it outputs what it sees on the screen. So far, so good.

However, none of the following works.
> camorama -d /dev/video1
'Could not connect to video device /dev/video1

> xawtv -c /dev/video1 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
xinerama 0: 1920x1200+1440+0
xinerama 1: 1440x900+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYMENU(id=134217738;index=0;name="60 Hz";reserved=3080712544): Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb6ac1dd0b7d27450 [PAL_I,PAL_D1,PAL_Nc,NTSC_M,NTSC_M_JP,?,SECAM_D,SECAM_K,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
Segmentation fault (core dumped)

> mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0991)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Device or resource busy
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

I could do the same with the v4l2 driver instead of v4l but with the same result.

Some more analysis:
> v4l-info /dev/video1 

### v4l2 device info [/dev/video1] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "uvcvideo"
	card                    : "UVC Camera (046d:0991)"
	bus_info                : "0000:00:1d.7"
	version                 : 0.1.0
	capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "Camera 1"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 1
	description             : "MJPEG"
	pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
	index                   : 1
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "YUV 4:2:2 (YUYV)"
	pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 176
	fmt.pix.height          : 144
	fmt.pix.pixelformat     : 0x47504a4d [MJPG]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 0
	fmt.pix.sizeimage       : 50688
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "Brightness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 128
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
	id                      : 9963777
	type                    : INTEGER
	name                    : "Contrast"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 32
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
	id                      : 9963778
	type                    : INTEGER
	name                    : "Saturation"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 32
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
	id                      : 134217728
	type                    : INTEGER
	name                    : "Backlight Compensation"
	minimum                 : 0
	maximum                 : 2
	step                    : 1
	default_value           : 1
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
	id                      : 134217729
	type                    : MENU
	name                    : "Power Line Frequency"
	minimum                 : 0
	maximum                 : 2
	step                    : 1
	default_value           : 2
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
	id                      : 134217730
	type                    : INTEGER
	name                    : "Sharpness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 224
	flags                   : 0

### video4linux device info [/dev/video1] ###
general info
    VIDIOCGCAP
	name                    : "UVC Camera (046d:0991)"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 0
	maxheight               : 0
	minwidth                : 48
	minheight               : 32

channels
ioctl VIDIOCGCHAN: Invalid argument

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32896
	hue                     : 0
	colour                  : 8224
	contrast                : 8224
	whiteness               : 0
	depth                   : 0
	palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 176
	height                  : 144
	chromakey               : 0
	flags                   : 0


Some IO system calls are obviously not working, but what does this mean in my situation?

Oh yes, and I have the latest uvcvideo drivers installed, revision 244.

Relevant modules:
> lsmod | grep uvc
uvcvideo               58116  1 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  2 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  7 snd_usb_audio,uvcvideo,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

Related threads, but they don't help:
[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727)
[http://ubuntuforums.org/showpost.php?p=4299269&postcount=22](http://ubuntuforums.org/showpost.php?p=4299269&postcount=22) (comes closest)
[http://ubuntuforums.org/showthread.php?t=118517&p=963173](http://ubuntuforums.org/showthread.php?t=118517&p=963173) (I guess same problem but unanswered)

So, do I simply have to accept that neither camorama, xawtv, nor skype work? Let alone vlc, mplayer and ffmpeg. Would loading other modules help? Which ones? Am I doing something wrong? :confused:

---

### Post by untill on 2008-08-25
Anyone?:-?

---

### Post by TaTaE on 2008-09-07
same problem here. webcam used to work perfectly in hardy heron. After i moved to Intrepid, webcam only works with ekiga. Gstreamer seems to hate it. Cheese, skype, camorama also don't work.

---

### Post by felixq78 on 2008-09-20
:guitar:
The solution is simple, if you have a dual boot system, USE M$ XP.
I'm not a patient person, I use products/systems that work, if they don't I simply shop elsewhere.
I like Linux operating systems but if they want the world to take them seriously then they'll have to pull up their socks.
If Linux worked as well as it should, then the whole concept of "Dual boot OS" wouldn't exist.
Why else would you use Microsoft operating systems?
It's obvious that most people use Microsoft operating systems for two reasons, 
(1) Pure ignorance, I.E, they aren't aware that they have an alternative choice, they think that the operating system is an integral part of their computer.
(2) They are forced to because of Gates and his corporate fascist methods.
Gates only succeeds because the open source community has been way too lazy.

---

### Post by TaTaE on 2008-09-20
I have asked a technical question and i don't want political answers. I want bugs to be repaired because i am too lazy to switch back to windows. Using Windows is too complicated for my usual tasks because it is a too rudimentary OS.

---

### Post by thirstyghost on 2008-09-20
Have you tried it through Cheese or Skype?

I also assume you've tried booting up with the camera already plugged in.

Check Synaptic to see if the "gspca" drivers are installed.

Your USB id number for that model isn't listed in this compatibility chart:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

That's all I can think of, sorry.

---

### Post by xxernestoxx on 2008-09-22
> **felixq78 said:**
> :guitar:
The solution is simple, if you have a dual boot system, USE M$ XP.
I'm not a patient person, I use products/systems that work, if they don't I simply shop elsewhere.
I like Linux operating systems but if they want the world to take them seriously then they'll have to pull up their socks.
If Linux worked as well as it should, then the whole concept of "Dual boot OS" wouldn't exist.
Why else would you use Microsoft operating systems?
It's obvious that most people use Microsoft operating systems for two reasons, 
(1) Pure ignorance, I.E, they aren't aware that they have an alternative choice, they think that the operating system is an integral part of their computer.
(2) They are forced to because of Gates and his corporate fascist methods.
Gates only succeeds because the open source community has been way too lazy.
Really? I blame the lack of vendor support, most vendors do not release the source for the drivers to their products. You can not release a driver for something if the manufacture does not help you in any way. Many community development groups have sent open letters to vendors stating they would code and develop open source drivers for free. It would help if PC builders like D3LL or G4teway would push their vendors to release the driver source at least even if they did not work with community developers. One thing though please don't call the community lazy seriously...these people are smart and organized. If they were lazy like you say so many great distributions would not exist. If you don't like the way things work go back to m$ and never come back attitudes like yours are why people don't take Linux seriously not the dedication of our developers or lack there of as you say. Oh and if you really are going to post, reply with an answer to the question asked not a mediocre criticism to a question which was never asked.

[http://kerneltrap.org/node/7636](http://kerneltrap.org/node/7636)
[http://www.kroah.com/log/linux/free_drivers.html](http://www.kroah.com/log/linux/free_drivers.html)

-------------------------------------------------------------------------
I have a quickcam and this tarball fixed the problem for me,
[http://qce-ga.sourceforge.net/#download](http://qce-ga.sourceforge.net/#download)
it is an open source driver for most quickcam models, I know this cam is compatible with linux my other pc that runs mandriva picked it up as soon as i plugged it in no need for additional driver instalation.

---

### Post by TaTaE on 2008-09-22
Reading more carefully what people said in upper posts, would save everyone a lot of time.
I just said that my webcam DOES work with ekiga perfectly in Intrepid. It has worked perfectly in Hardy with ANY APPLICATION. Now it doesnt with skype and cheese and everything else besides EKIGA.

Cheers xxxernestxx

---

### Post by untill on 2008-11-21
Solved in 8.10. Now It Just Works out of the box. Thanks all for your help.

---

### Post by TaTaE on 2008-11-22
yep, solved

---

### Post by vanquishedangel on 2008-11-22
I found a solution that I am posting all over because I found a needle in a haystack I will paste it here:


I hope this is not too late but I have been tirelessly looking to get my webcam to work in ubuntu intrepid 8.10 to the point of pulling my hair out but I didn't give up and if this doesn't help you then maybe it will help someone like me but I found this on another web page and compiled it from others and it worked like a dream, I will copy and paste the article

The only way I have managed to make totem show the videos was to set the output on the video tab of gstreamer-properties to "X Window System (No Xv)".

How to change the properties in gstreamer: press alt, f2. Then type gstreamer-properties, then go to the video tab and under default imput change the plugin to "x window system ( no xv)" Now start cheese.

---

### Post by josvanr on 2008-12-13
nope not solved. I just updated from hardy to intrepid, but the cam still doesn't work. When I start camstream and choose the cam, a little black screen appears (a small screen). When I then try to choose another resolution, camstream hangs alltogether. 

(btw, kde4 is a disaster, i'm going back to debian/fvwm)

---

### Post by Tryfon on 2008-12-14
People, I have Ubuntu 8.10 and Logitech QuickCam Pro and it works only with aMSN. Camorama tells me "Could not connect with video device. Please check connection." and Cheese Webcam Booth just doesn't show anything, stucks when I try to capture anything and then refuses to quit. Still when I open Cheese I notice that my webcams light turns on. 

Help please!

---

### Post by seaq on 2008-12-16
Hi, i've put in the wiki a list for known bugs with webcam cameras. 


[https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams)

---

### Post by SteveDean on 2009-04-15
I know this is an on going problem, but has anyone answered the question of how to get a quickcam to work with 8.10 and aMSN?

Failing that, can anyone recommend a camera that definitely does work, with 8.10 AND in aMSN?

Thanks in advance.

---

