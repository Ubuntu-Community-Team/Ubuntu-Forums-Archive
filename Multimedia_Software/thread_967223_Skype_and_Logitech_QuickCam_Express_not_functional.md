---
title: "Skype and Logitech QuickCam Express not functional"
date: 2008-11-01
forum: Multimedia Software
---

### Post by JBotAlan on 2008-11-01
Hello,

I am attempting to get my Logitech QuickCam Express working with Skype on my Ubuntu 8.10 system.

I plugged it in and right "out-of-the-box", it works with XawTV and Cheese. However, I can't seem to get it to open with VLC--in the terminal, I always get a "v4l2 demux error: invalid tuner 0." if I try to open the camera's input (/dev/video0) using Video for Linux 2. No video output shows in VLC, and the timer shows up as if playing an audio file. If I try to open the stream with Video for Linux, I intermittently get a screen full of scrambled colors or just a black screen, and a whole lot of errors at the terminal ("v4l demux error: failed capturing new frame"). This is almost exactly the result I see when attempting use with Skype--when I select the video device and press "Test", I sometimes get flickering gibberish in the preview window, and other times the preview window stays black. Skype doesn't allow me to change any specific details, so I don't have much to toy with here. VLC, on the other hand, has a ton of settings, none of which seem to fix anything.

Version numbers and other technical details:
[LIST]
[*]I am using Skype version 2.0.0.72, the latest from what I can tell.
[*]My camera shows up like this when I use lsusb:
```
Bus 002 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
```
[*]This is the dmesg output from plugging in my camera:
```
[ 9799.473100] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 9799.668435] usb 2-2: configuration #1 chosen from 1 choice
[ 9799.670228] gspca: probing 046d:092f
[ 9799.770178] gspca: probe ok
```
That would lead me to believe the gspca driver is handling my camera.
XawTV uses the spca561 driver, though--that is what's displayed on the options panel.
[*]XawTV outputs the following to my terminal; it works great.
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-7-generic)
xinerama 0: 1024x768+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
```
[*]Telling XawTV to open /dev/video0 (which, according to the manual page should disable Xvideo support...I don't fully understand, but I figured I'd drop as many clues as I could) works great, also.
[*]I have seen nothing but strange behavior from Skype: anything from a freeze to just randomly terminating when I click "Test". I don't know what to make of this at all.
[*]I tried using gstfakevideo to open the camera and format it properly for Skype, but I don't fully understand how to use gstfakevideo, and I have no way of testing it from another program--I want to know if the stream gstfakevideo creates is functional. I will continue to pursue this path, but so far it has proven fruitless.
[/LIST]

I would appreciate any suggestions...I want to get this working, and from what I understand it worked before 8.10.

JBot

---

### Post by beauman on 2008-11-02
Hi!

I like to know, if your cam works in ekiga.

On my laptop, the build-in cam does work in ekiga,
but not in skype. I guess it's a problem of skype.

But maybe somebody knows a work-around?

Regards, beauman

---

### Post by JBotAlan on 2008-11-02
> **beauman said:**
> I like to know, if your cam works in ekiga.

Indeed it does seem to work with Ekiga. I was able to open it and see myself in the preview window.

Once I get some free time, I will have to toy with gstfakevideo, as it seems to be the only easy alternative at this point. But it certainly seems that Skype is the culprit here. I would, however, love to have an explanation as to why VLC cannot open my camera's stream...

JBot

---

### Post by JBotAlan on 2008-11-02
gstfakevideo did it for me.

I honestly cannot remember how I installed it. I may have gotten it through Synaptic Package Manager, but I vaguely recall downloading it and compiling it by hand. But I might be lying...don't quote me on this one.

However, I ran gstfakevideo (after poking around in the script for a bit to figure out how it works) as follows:
```
gstfakevideo v4l2src device=/dev/video1
```
I didn't even know v4l2src was an option until reading a lot. v4lsrc would never work properly, but v4l2src works great. Skype launched, I clicked "Test", and it is beautiful.

Note: my camera is on /dev/video1. I did that by executing
```
sudo mv /dev/video0 /dev/video1
```
Since apparently gstfakevideo cannot work with any other device than /dev/video0.

Hopefully that works for others. And hopefully at some point Skype will fix this so it works natively.

Oi! Linux is fun! ;-)
JBot

---

### Post by JBotAlan on 2008-11-02
I have yet to figure out how to make the camera driver not go back to /dev/video0 on boot. I will do some more research and probably post back here.

---

### Post by Vadi on 2009-03-01
Thanks for your work here.

---

### Post by xopher_mc on 2009-08-26
Found that this works (used the method detailed here in 32bit ubuntu but found it a pig in 64bit as had gtskvideo had compilation errors).  Found the method detailed [here]("http://lglinux.blogspot.com/2008/10/skype-and-logitech-webcam-in-ubuntu.html") works 

sudo apt-get install lib32v4l-0 libv4l-0

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

:)

---

