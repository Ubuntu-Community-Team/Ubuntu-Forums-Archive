---
title: "Webcam no longer works"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by linuxonbute on 2007-08-09
I installed ekiga recently and my webcam worked fine

(Ubuntu 7.04 creative webcam notebook0

Yesterday I installed aMSN so I could chat with video to my sons who use MS Windows.

Now the webcam won't work with either ekiga or aMSN.

tail -f /var/log/messages gives the following when I plug the camera in :

Aug  9 16:58:42 mainbox kernel: [ 9479.124276] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 

Settings/device manager shows 
Unknown USB device (0x401f)
info.udi  string /org/freedesktop/Hal/devices/usb_device_41e_401f_noserial
info.vendor string Unknown(Ox041e)

cat /proc/devices:
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 81 video4linux
 99 ppdev
116 alsa
128 ptm
136 pts
180 usb
189 usb_device
254 usb_endpoint

lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 007: ID 041e:401f Creative Technology, Ltd Webcam Notebook
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:2f11 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

lsmod  ( part )
gspca                 606160  0 
videodev               27136  3 ov511,zc0301,gspca
v4l2_common            24192  2 zc0301,videodev
v4l1_compat            14340  1 videodev
usbcore               131480  7 usblp,ov511,zc0301,gspca,ehci_hcd,uhci_hcd

Does anyone have any idea what happened?
And does anyone know how I can fix it please?
tia

---

### Post by linuxonbute on 2007-08-09
I have uninstalled both aMSN and ekiga and then re-installed ekiga but it has made no difference.

---

### Post by linuxonbute on 2007-08-10
Well it now seems to work.

I read of some problems in another thread which got me thinking that it was something to do with the kernel or kernel modules.

I was booting kernel 2.6.20-16-386

so re-booted and chose kernel 2.6.17-11-generic

and it worked.

Might try one of the others I have later.

Norman

---

