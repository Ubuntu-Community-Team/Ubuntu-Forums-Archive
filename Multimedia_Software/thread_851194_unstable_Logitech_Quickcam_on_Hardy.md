---
title: "unstable Logitech Quickcam on Hardy"
date: 2008-07-06
forum: Multimedia Software
---

### Post by achortleaday on 2008-07-06
I just updated to Hardy a few days ago, and I am having a terrible time trying to make everything work again. My webcam (Logitech Quickcam) was working decently fine using uvcvideo on Gutsy. Now, however, I am having really strange instability issues. I have the newest uvcvideo driver installed and lsusb recognizes my camera, and about 1/3 of the time (usually in the morning, of course, when I'm not actually using skype) when I boot up my computer it works fine, but then a few hours later, or when I come back, it stops working, along with the other 2/3 of the time when it doesn't work at all.

Skype does one of three things (and I cannot for the life of me figure out why these happen when they do, it seems random):
-Stops seeing that I have a camera ('no device found')
-Sees I have a camera but when I try to test it, the camera doesn't turn on
-Sees I have a camera, turns it on, but then displays a black screen.

Generally when these happen in Skype, Cheese also stops seeing my camera, and literally, it will happen after me doing NOTHING to my drivers or anything, often while the computer is sitting completely untouched.
Help please?

---

### Post by Resnick on 2008-07-07
Hey achortleaday. I am sorry I cannot personally help as I am having a similar problem to the one you described. But I thought you might need a cam-troubles-buddy and pool our resources :D Here are my details;

8.04 LTS working with a Logitech Quickcam Communicate MP Plus;

> $ uname -a
Linux sleepy 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

> $ lsusb
Bus 003 Device 003: ID 046d:09a1 Logitech, Inc.

> $ dmesg
...
[  257.562386] usbcore: deregistering interface driver uvcvideo
[  262.337212] Linux video capture interface: v2.00
[  262.342933] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
[  262.358919] usbcore: registered new interface driver uvcvideo
[  262.358927] USB Video Class driver (v0.1.0)

> $ lsmod | grep uvc
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  7 uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd

With cam active via luvcview;
> $ lsmod | grep uvc
uvcvideo               58116  1 
...
videodev               29440  2 uvcvideo
...

> $ /sbin/modinfo uvcvideo
filename:       /lib/modules/2.6.24-19-generic/ubuntu/media/usbvideo/uvcvideo.ko
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@skynet.be>
srcversion:     B02D7BEED9A4AC8CE60F5B6
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0200d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0102d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0100d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v090CpB371d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05ACp8300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05ACp8501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v041Ep4057d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0402p5606d*dc*dsc*dp*ic0Eisc01ip00*
depends:        usbcore,videodev,v4l2-common,v4l1-compat,compat_ioctl32
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           trace:uint
> $ ls /dev/video*
/dev/video0


It's recognised by Skype and luvcview, and until I tried it a few minutes ago was working great with the uvcvideo kernel module. I had one issue where the colors became ultra-saturated, but was fixed by using luvcview to reset everything to defaults.

At this moment in time I suffer from the third issue you described "-Sees I have a camera, turns it on, but then displays a black screen." I believe microphone input still works though.

Sorry if I didn't provide detailed enough information, but I am fairly inexperienced in Linux and switch to Ubuntu only yesterday!

Good luck achortleaday. I will let you know if I find anything out. 

Any help is appriciated. Thanks guys and girls.

(P.S. I posted on the [Linux UVC]("http://developer.berlios.de/projects/linux-uvc/") project forums too [here]("http://developer.berlios.de/forum/message.php?msg_id=44411") if you want to keep any eye on that. I just switched from Slackware, but it's the exact same issue in Ubuntu for me at the moment)

---

### Post by Resnick on 2008-07-07
I just got done reading [http://openfacts.berlios.de/index-en.phtml?title=Linux%20UVC]("http://openfacts.berlios.de/index-en.phtml?title=Linux%20UVC"), and it appears there are some known problems with some Logitech cameras.

> 
Some Logitech cameras suffer from a hardware/firmware bug which causes them to stop responding after a while. The exact nature and cause of the bug is still unclear. Supposedly Logitech knows about it and will fix their future webcams. There are patches floating around which attempt to work around the bug, tho they tend not be kept uptodate with the main source

They give links to a couple of the patches there but I haven't tried them yet.I actually unlugged the cam and tried it on a front port to no avail, but after I unloaded the modules uvcvideo and snd_usb_audio (as per some instructions on that page) and re-attached the camera to the rear USB port I find it now works again :confused:

---

