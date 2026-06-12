---
title: "Webcam woes"
date: 2009-10-28
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2009-10-28
Anybody got any ideas? 

mark@Lexington-19:~$ dmesg | grep gspca
[   21.801550] gspca: main v2.3.0 registered
[   21.894603] gspca: probing 0545:808b
[   22.640367] gspca: probe ok

mark@Lexington-19:~$ lsmod | grep gspca
gspca_tv8532           19584  0 
gspca_main             29952  1 gspca_tv8532
videodev               41600  1 gspca_main

and

mark@Lexington-19:~$ dmesg | grep usb

[   22.640411] usbcore: registered new interface driver tv8532
[   25.983503] usb-storage: device scan complete
[   25.984382] usb-storage: device scan complete
[   25.989336] usb-storage: device scan complete
[ 1752.491318] gspca: usb_submit_urb [0] err -28
[ 3211.903697] gspca: usb_submit_urb [0] err -28
[ 3362.019365] gspca: usb_submit_urb [0] err -28
[ 3373.979395] gspca: usb_submit_urb [0] err -28
[ 3391.103168] gspca: usb_submit_urb [0] err -28
[ 3406.487320] gspca: usb_submit_urb [0] err -28

doing:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama

does not work, along with camgrab, cheese, xawtv, camorama, gqcam, effectv and skype.

any ideas?

---

