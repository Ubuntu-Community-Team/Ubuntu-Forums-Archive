---
title: "Philips SPC1000NC Webcam crashes and doesn't work with skype"
date: 2008-07-02
forum: Multimedia Software
---

### Post by lucebike on 2008-07-02
Hi,

I just bought a Philips SPC1000NC Webcam, planning to use it for skype.
At first it wouldn't work at all; after I updated my uvcvideo to the current svn-version xawtv and luvcview now have an image, whereas camorama does not (Could not connect to video device (/dev/video0). Please check connection.)
But after some minutes (I have not yet found a pattern), the camera suddenly doesn't work any more; e.g. xawtv gives, when started the error

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.20-16-generic)
xinerama 0: 1024x768+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

Plugging out and in, the camera resumes to work (again only for some time).
If I run v4l-conf before that error occurs, I get 

v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xc0000000
/dev/video0 [v4l2]: no overlay support

Now Skype (I have version 2.0.0.68 ) lets me select my webcam (Options / Video Devices), but the test-image is just a green screen with some flickering black-and-white stripes at the top.
However, skype works fine with my other video device /dev/video1, which is a tv-card.


lsusb gives
Bus 001 Device 005: ID 0471:0332 Philips

and dmesg shows
[ 3860.998643] usb 1-2: USB disconnect, address 7
[ 3861.262445] usb 1-2: new high speed USB device using ehci_hcd and address 8
[ 3861.425163] usb 1-2: configuration #1 chosen from 1 choice
[ 3861.425617] uvcvideo: Found UVC 1.00 device Philips SPC 1000NC Webcam (0471:0332)
[ 3861.434154] input: Philips SPC 1000NC Webcam as /class/input/input12
[ 3861.461675] 8:3:1: cannot get freq at ep 0x84
[ 3862.281570] 8:3:1: cannot get freq at ep 0x84

This freq-error at the end does, according to some forum entries I read, not mean any harm and occurs sometimes with a working camera, too.

Thank you very much for your help!
Lucebike

---

### Post by lucebike on 2008-07-02
Well, just now (without me changing anything!) something weird started to happen:

The camera *does* work with skype (yehaa), but only for some time... after that, it changes the device, i.e. if it was /dev/video1 before, it is /dev/video2 afterwards, if it was video2, it becomes video3 (that is how far I have gotten). Restarting skype, the camera then works under the new device - or it does not and switches device again.

Ok, this is better then before, I couldn't test the perfomance during a real skype call yet. Still, I would prefer a camera working that is not constantly trying to elude me.

---

