---
title: "Quickcam for Notebooks Pro - Not working"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by Spitphire on 2007-12-23
Hello,

I'm having some troubles with my webcam, basically I cannot get it to work.  My linux experience is limited.  My webcam is a Logitech Quickcam for Notebooks Pro.  I tried installing the uvc drivers; but it still is not working.  Any other experiences and/or sugestions would be helpful. Thanks.

Here is some output:


am@lp:~$ uname -a
> 
Linux lp 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


am@lp:~$ lsusb
> 
Bus 004 Device 011: ID 046d:08c3 Logitech, Inc. 


am@lp:~$ lsmod |grep -i video
> 
video                  18060  0 
uvcvideo               54660  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  3 quickcam,uvcvideo,via_v4l_drv
v4l2_common            18432  2 uvcvideo,videodev
v4l1_compat            15364  2 uvcvideo,videodev
usbcore               138632  8 quickcam,snd_usb_audio,snd_usb_lib,uvcvideo,usbhid,ehci_hcd,uhci_hcd


am@lp:~$ dmesg | grep -i uvcvideo
> 
[   47.528000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
[   48.528000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[   49.528000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[   49.528000] uvcvideo: Failed to initialize the device (-5).
[   49.528000] usbcore: registered new interface driver uvcvideo


---

