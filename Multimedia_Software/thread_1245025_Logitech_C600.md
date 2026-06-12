---
title: "Logitech C600"
date: 2009-08-20
forum: Multimedia Software
---

### Post by old_dope on 2009-08-20
I already have a Logitech webcam but i'm fed up with the head phone and cables. So i've been looking at the Logitech C600 with it's built-in microphone etc. So, could i ask if anyone has used this webcam and if there were any problems with install, set-up, and actually running it. Thanks

---

### Post by oluapSissa on 2009-08-31
Hi,

The Camera works out of the box in Ubuntu, it is a UVC camera so it uses the excellent linux uvc driver.
The mic is also very good, unlike previous logitech models it supports a large variety of sample-rates.

Best regards,
Paulo

---

### Post by ladyhawk54 on 2009-10-09
Hi Paulo,
I've just installed the C600 webcam and the video came right up, but i've been tweaking for 2 days to get the audio thru the cam, but can't get it to work, so i still have to use my head set:( Can you **please** help me figure out what settings i am obviously overlooking or have wrong?
Thank you so much in advance!
Roberta

---

### Post by nate1010smith on 2009-12-03
I'm having some issues with the logitech c600 as well. I have yet to try using the camera as an audio source but have had some problems with video.

If I anyone wants more information, please let me know.

**In relation to the audio problems:**

**/var/log/messages:**
Dec  3 18:13:19 e310 kernel: [1631067.892024] usb 1-1: new high speed USB device using ehci_hcd and address 60
Dec  3 18:13:19 e310 kernel: [1631068.239492] usb 1-1: configuration #1 chosen from 1 choice
Dec  3 18:13:19 e310 kernel: [1631068.239836] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0808)
Dec  3 18:13:19 e310 kernel: [1631068.274234] input: UVC Camera (046d:0808) as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input10
Dec  3 18:13:20 e310 kernel: [1631068.904029] usb 2-2: new full speed USB device using uhci_hcd and address 67
Dec  3 18:13:20 e310 kernel: [1631069.472285] usb 2-2: new full speed USB device using uhci_hcd and address 68
**Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.**
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 pulseaudio[22192]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Dec  3 18:13:21 e310 kernel: [1631070.044274] usb 2-2: new full speed USB device using uhci_hcd and address 69
Dec  3 18:13:21 e310 kernel: [1631070.432041] usb 2-2: new full speed USB device using uhci_hcd and address 70

**The video problems:**

**Cheese works.**

**vlc returns:**
[0x86edf28] main input error: open of `v4l2:///dev/video0' failed: (null)
[0x87772d8] v4l2 demux error: invalid tuner 0.
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
[0x87772d8] v4l2 demux error: cannot get video input characteristics (Invalid argument)
[0x86ee0c0] v4l2 access error: invalid tuner 0.
libv4lconvert: warning more framesizes then I can handle!
libv4lconvert: warning more framesizes then I can handle!
[0x86ee0c0] v4l2 access error: cannot get video input characteristics (Invalid argument)

**Camorama -D returns:**
VIDIOCGCAP
device name = UVC Camera (046d:0808)
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32896
hue = 0
colour = 7196
contrast = 8224
whiteness = 0
colour depth = 0
**VIDIOCGMBF  --  could not set buffer info, exiting...**

---

### Post by marcsdb on 2009-12-09
Hi all,

are there any news about the video problem with Logitech Webcam C600 ( 046d:0808 )?
I have the same outputs on my debian amd64 system from camorama.
The system loads autmatically (w/o earlier configurations) the driver module uvcvideo.

The strange thing is, that this C600 cam works with skype on the same debain system incl. mike!
Other programs like camorama, camstream, webcam can not completely access the cam.

I don't know how to fix this problem.
Has anybody an idea or an approch to solve this problem?

Thank you in advance!
Marc

-----

Here my camorama output:

[FONT=Courier New][SIZE=1]VIDIOCGCAP
device name = UVC Camera ( 046d:0808 )
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 1600
max height = 1200
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 640
height = 480
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 800
height = 600
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32896
hue = 0
colour = 7196
contrast = 8224
whiteness = 0
colour depth = 16
YUYV
VIDIOCGMBF  --  could not set buffer info, exiting...[/SIZE][/FONT]

Log from /var/log/messages
[FONT=Courier New][SIZE=1]Dec  9 18:17:50 sandiego kernel: [67866.669313] usb 7-1: new high speed USB device using ehci_hcd and address 3
Dec  9 18:17:50 sandiego kernel: [67867.107307] usb 7-1: configuration #1 chosen from 1 choice
Dec  9 18:17:51 sandiego kernel: [67867.797236] usb 7-1: New USB device found, idVendor=046d, idProduct=0808
Dec  9 18:17:51 sandiego kernel: [67867.797236] usb 7-1: New USB device strings: Mfr=0, Product=0, SerialNumber=2
Dec  9 18:17:51 sandiego kernel: [67867.797236] usb 7-1: SerialNumber: A988CE50
Dec  9 18:17:51 sandiego kernel: [67867.801081] uvcvideo: Found UVC 1.00 device <unnamed> ( 046d:0800 )
Dec  9 18:17:51 sandiego kernel: [67867.846575] input: UVC Camera ( 046d:0808 ) as /class/input/input6
Dec  9 18:17:51 sandiego kernel: [67867.874859] usbcore: registered new interface driver uvcvideo
Dec  9 18:17:51 sandiego kernel: [67867.874865] USB Video Class driver (v0.1.0)[/SIZE][/FONT]

---

### Post by marcsdb on 2010-01-24
Hi Brian,

you have answered to my post by e-mail, why? I cannot answer to you via the online form!
Your message follows. Further answer see below.

----BEGIN----

This is a message from av8rbri at Ubuntu Forums ( [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php) ). The Ubuntu Forums owners cannot accept any responsibility for the contents of the email.

To email av8rbri, you can use this online form:
[http://ubuntuforums.org/sendmessage.php?do=mailmember&u=994738](http://ubuntuforums.org/sendmessage.php?do=mailmember&u=994738)


This is the message:

Hi there.  In a post about 4 wks. ago, you mentioned that your Logitech c600 works with Skype.

I cannot seem to get my cam going with Skype. It works with Ekiga, luvcview and cheese no problem at all.  When I hit the test button, just black screen in skype.....

I am running 8.04 [Hardy] and version of skype is 2.1.0.47

the lsusb is:  Bus 001 Device 004: ID 046d:0808 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 


Do you have any tips or tricks to get this cam running?  It seems like a good cam and the auto lighting works well.

I would love to see my family online.

Thanks.
Brian.

----END----

I have no idea what your problem is.
I use Debian 5 and Skype 2.0.0.72, und there is no problem.
This could be a work-around: 
Maybe your skype tries to use another interface of the C600. It must use mmap() to get the image from the cam. Try to get this info with following skype call
> strace skype

You get back very much info incl. interface calls. Maybe you can locate the problem in such way.

Greetings
Marc

---

### Post by balta2ar on 2010-03-05
I'm experiencing similar troubles with Logitech C600.

It works on the lowest resolution only - 176x144.



[bz@bolt ~]$ mplayer tv:// -tv device=/dev/video:width=800:height=600
MPlayer SVN-r30526-4.4.3 (C) 2000-2010 MPlayer Team
142 audio & 332 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: UVC Camera (046d:0808)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 176x144 => 176x144 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
v4l2: ioctl set mute failed: Invalid argument
v4l2: 28 frames successfully processed, 27 frames dropped.

Exiting... (Quit)



Cheese successfully shows preview in resolutions up to 800x600, which are not highest for this cam. However recording fails, the program hangs up after pressing Start record button.



[bz@bolt src]$ sudo camorama -D -d /dev/video

VIDIOCGCAP
device name = UVC Camera (046d:0808)
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 176
max height = 144
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 160
height = 120
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 160
height = 120
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 32896
hue = 0
colour = 7196
contrast = 8224
whiteness = 0
colour depth = 0
VIDIOCGMBF  --  could not set buffer info, exiting...



vlc is also able to show preview but in lowest resolution only as well. If I change any of Advanced parameters, it reports error:
[0x8b2cde8] v4l2 demux error: invalid tuner 0.
[0x8b2cde8] v4l2 demux error: invalid tuner 0.
[0x88e9038] v4l2 access error: invalid tuner 0.
[0x88e9038] v4l2 access error: invalid tuner 0.
[0x88e8ca8] main input error: open of `v4l2:///dev/video' failed: (null)




xawtv shows preview but aborts when I try to start recording from camera.

[bz@bolt src]$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.32-ARCH)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x807bff0 [PAL_I,PAL_D,PAL_D1,PAL_K,PAL_M,PAL_N,PAL_Nc,PAL_60,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
Segmentation fault



P.S. I'm not sure if it matters but I'm using Compiz.

---

