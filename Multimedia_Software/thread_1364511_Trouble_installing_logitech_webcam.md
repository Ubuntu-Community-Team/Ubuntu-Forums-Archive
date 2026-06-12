---
title: "Trouble installing logitech webcam"
date: 2009-12-26
forum: Multimedia Software
---

### Post by Jlsheets on 2009-12-26
Hello all,

I'm very new to Ubuntu and to using the terminal to make things work. I've been trying to install a logitech webcam c250 for the past couple days and have had no success. I've searched the forums and I know this question has been asked before for other webcams but I can't find anything that works. 

When I run the commands in the terminal that are used to get the required packages to install this webcam (apt-get install module-assistant camorama xawtv gspca-source spca5xx-source qc-usb-source) I consistently get the error gspca-source not found (not sure if that's the exact error). So if anybody can shed some light on this thanks.

jared

---

### Post by david_2001 on 2009-12-26
The Logitech c250 is a UVC webcam and it works out of the box with 9.10 (I've got one, so I know).  To check whether it has been detected, you could try either:
```

david@first-desktop [~]
$ dmesg | grep uvc
[    9.520027] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0804)
[    9.549209] usbcore: registered new interface driver uvcvideo
```
or
```
david@first-desktop [~]
$ lsmod | grep uvcvideo
uvcvideo               69100  0 
videodev               42752  4 uvcvideo,tuner,saa7134,v4l2_common
v4l1_compat            18276  2 uvcvideo,videodev
usbcore               183764  11 snd_usb_audio,snd_usb_lib,uvcvideo,usbhid,dvb_usb_dib0700,dvb_usb,usb_storage,lirc_mceusb,uhci_hcd,ehci_hcd
```
If you get a positive result, install cheese, run it and see what it finds...

---

### Post by Jlsheets on 2009-12-26
It has been detected and when I run cheese it work. The video seems to work pretty well (kind of sluggish). The only problem I am having is sound output when I talk using Skype. My voice records fine when using cheese but when I use Skype the people I talk told me they can not hear my voice. Any tips?

Thanks for the help,

Jared

---

