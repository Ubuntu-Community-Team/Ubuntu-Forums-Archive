---
title: "Problem with Luvcview"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by SamMessing on 2008-01-30
I recently purchased a logitech quickcam pro 9000 webcam, and am attempting to get the camera to work. It seems like most people have been able to get it to work using the program luvcview, but I have not, as of yet.

When I try to run luvcview in a terminal, the camera turns on, and then I get the following errors:

```
luvcview 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

I have attempted to install the uvc drivers using the following tutorial: [http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC]("http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC")

Does anyone have suggestions of what I can try to get luvcview to work? and to make sure that I installed the uvc drivers properly?


Just so you have the info:

lsusb:
```
Bus 007 Device 007: ID 046d:0990 Logitech, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 011: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 010: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

lsmod | grep uvc:
```
uvcvideo               52228  0 
compat_ioctl32         11136  1 uvcvideo
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbcore               161584  6 snd_usb_audio,uvcvideo,snd_usb_lib,ehci_hcd,uhci_hcd

```

Any help would be greatly appreciated!

---

### Post by SamMessing on 2008-01-31
bump

---

### Post by Mustard on 2008-02-28
Have a read through this thread and you will find a link to an alternative to lucview that worked for me.
[http://ubuntuforums.org/showthread.php?t=678098](http://ubuntuforums.org/showthread.php?t=678098)

---

