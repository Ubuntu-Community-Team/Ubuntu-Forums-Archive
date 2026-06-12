---
title: "Webcam Help!! I've tried everything"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by Kartik Babu on 2006-02-06
Hi,
  I have a Labtec Pro Webcam and Im trying to get it to run under  2.6.12-10-686 . I've tredged through the forums looking for pointers and have tried almost everything.
  I used the spca5xx modules available from [http://mxhaard.free.fr/](http://mxhaard.free.fr/) which i suppose is the widely accepted source. The newly compiled module is loaded.

I do xawtv -hwscan and I get this

[COLOR="Red"]kbabu@workhorse:~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-686)
looking for available devices
port 61-61
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l
    name : Labtec Webcam Pro
    flags:  capture

[/COLOR]

I try to use spcaview and this is what I get:
[COLOR="Red"]spcaview -d /dev/video0 -f jpg -l
 Spcaview version: 1.1.5 date: 12:12:2005 (C) [email]mxhaard@magic.fr[/email]
Initializing SDL.
Could not initialize SDL: No I/O port permissions.
[/COLOR]

if I use suso with spcaview, my whole screen goes black and everything just hangs.

xawtv -device /dev/video0 also gives me a black window, but does not hang. I read on the box that the webcam has a resolution of 640x480 but this is what xawtv is trying to do:

[COLOR="Red"]kbabu@workhorse:~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-686)
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=144;width=176;format=7): Invalid argument
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
ioctl: VIDIOCMCAPTURE(frame=0;height=144;width=176;format=9): Invalid argument
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
ioctl: VIDIOCMCAPTURE(frame=0;height=144;width=176;format=1): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=144;width=176;format=13): Invalid argument
no way to get: 384x288 32 bit TrueColor (LE: bgr-)
[/COLOR]

the caption on the window however shows a much higher resolution: 1680x1050 32-bit truecolor . how do I go about configuring this?

---

### Post by Kimm on 2006-02-07
you need yo have SDL installed... I gather from your error's that you dont, search for "sdl" in synaptic and install it

---

