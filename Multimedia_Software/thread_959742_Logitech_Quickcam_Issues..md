---
title: "Logitech Quickcam Issues."
date: 2008-10-26
forum: Multimedia Software
---

### Post by iain_colin on 2008-10-26
Long story so bear with.

On 7.04 i used to be able to use my Logitech Quickcam Express (046d:0840) without installing any drivers. Apparently now however i needed to install qc-webcam (qce-ga.sourceforge.net/)

That went fine, and the webcam driver successfully installed. The problem i have now is that it cannot be accessed by any program, otherwise it locks up. I have tried Ekiga, aMSN, Camorama, XawTV and they all do the same thing. The only solution i have found so far is thus:

1. Use VirtualBox to load up Windows XP
2. Attach the webcam "virtually" to Windows XP.
3. Turn the virtualbox off, and modprobe quickcam

And for some reason it then works in all programs.

Can anyone suggest what the problem is?

lsusb
Bus 002 Device 005: ID 0951:1603 Kingston Technology 
Bus 002 Device 004: ID 07d1:3c07 D-Link System 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 001 Device 003: ID 046d:c315 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


v4l-info
### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "Logitech QuickCam USB"
	type                    : 0x201 [CAPTURE,SUBCAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 360
	maxheight               : 296
	minwidth                : 32
	minheight               : 32

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Camera"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32768
	hue                     : 32768
	colour                  : 32768
	contrast                : 32768
	whiteness               : 32768
	depth                   : 32
	palette                 : RGB32

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 176
	height                  : 144
	chromakey               : 0
	flags                   : 524288

dmesg
[   29.833585] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   29.833588] quickcam: Kernel:2.6.24-19-generic bus:1 class:FF subclass:FF vendor:046D product:0840
[   29.868585] quickcam: Sensor HDCS-1000/1100 detected
[   29.874592] quickcam: Registered device: /dev/video0
[   29.874609] usbcore: registered new interface driver quickcam

---

