---
title: "can't get chicony webcam to work"
date: 2008-04-25
forum: Multimedia Software
---

### Post by justin_acklin on 2008-04-25
I just install ubuntu 8.04 64 bit on a gateway p-6831fx.  It has a builtin Chicony webcam.  

lsusb:
Bus 007 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0a5c:2101 Broadcom Corp. 
Bus 005 Device 002: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  


I checked out the latest source for uvc, the only webcam drivers that I could find that support the Chicony cameras.  Built and installed the module ok, it loads fine:

justin@justin-ubuntu:/etc/network$ lsmod |grep uvc
uvcvideo               62600  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbcore               169904  10 hci_usb,snd_usb_audio,snd_usb_lib,usbhid,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd


But camorama still says 
Could not connect to video device (/dev/video0)

What am I missing here??

thanks...

---

### Post by spraveenitpro on 2008-04-25
Hi 

I have a Compaq C768TU machine with the Chicony Webcam integrated,
can't get it to work under Hardy, any idea how to get the Dog running..?

Praveen  ):P

---

### Post by justin_acklin on 2008-04-25
bump....anyone? nobody?

---

### Post by justin_acklin on 2008-04-27
Got it working.  The problem is with camorama -- xawtv and skype linux both work fine.  Camorama still says can't open /dev/video0

*shrug*

---

