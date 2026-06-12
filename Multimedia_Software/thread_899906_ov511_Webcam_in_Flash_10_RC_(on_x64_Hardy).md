---
title: "ov511 Webcam in Flash 10 RC (on x64 Hardy)"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Usufruct on 2008-08-24
So, I'm using Flash 10 RC on Hardy x64 with nspluginwrapper - it works great.  I do however have the issue that flash-based chat sites (such as stickam) do not seem to recognize my webcam (Creative PD1030 working with the ov511 driver).   

```
blong@blong-laptop:~$ lsusb | grep -i webcam
Bus 002 Device 006: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
blong@blong-laptop:~$ lsmod | grep ov511
ov511                  89268  0 
videodev               30720  1 ov511
usbcore               169904  5 ov511,hci_usb,ehci_hcd,uhci_hcd

```

I understand that flash 10 now has support for V4L2 devices... but I don't think ov511 is V4L2, unless I'm mistaken.  Flash 9 doesn't detect my webcam (and flashcam reports there are no V4L2 capture devices found).  I have had no luck with beta 1, 2 and now RC.  

So my question is, is there something simple I'm not grasping here?  I would very much like to be able to use my webcam with flash.  Anybody know if the ov511 driver is buggy with flash on 64 bit Ubuntu?

---

### Post by loell on 2008-08-24
if i'm not mistaken the v4l2 support for flash is not complete yet.

how about using **flascam** to bridge your v4l2 webcam to flash ;)

---

### Post by Usufruct on 2008-08-24
> **loell said:**
> if i'm not mistaken the v4l2 support for flash is not complete yet.

how about using **flascam** to bridge your v4l2 webcam to flash ;)

I guess I wasn't clear enough in my post.  Flashcam does not see the ov511 as a V4L2 device.  

```
blong@blong-laptop:~$ flashcam -L
Scanning devices
------
------
No V4L2 capture devices found.

```

---

### Post by Usufruct on 2008-08-25
I sent a video message to my dear sweet grandma, I know the camera works :)

(bump)

---

### Post by patrickballeux on 2008-08-26
Hi,

EDIT:  A project was created, see [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/").  It is a new software that creates a virtual webcam with tons of options and special effects.

OV511 is a V4L device.  If you want to use your webcam with Flash, I can suggest these softwares:

- AVLD
- Flashcam (for the vloopback module)
- Vloopback (the original)
- ucanvcam (I was not able to make it work with AMD64...)


Another way would be to screencast your desktop and show your webcam with Cheese or Camorama.  

You will need recordMyDesktop, ffmpeg, Vloopback (from flashcam) and mjpetools_yuv_to_v4l.

See my blog : [http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html](http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html)

(sorry, in french)

You fill find the link and the script to be able to do that.

What you could do also is to read you webcam with ffmpeg (ffmpeg -i /dev/video0) and pipe (as in the script) with mjpegtools_yuv_to_v4l.  It would probably work.

Good luck!

---

