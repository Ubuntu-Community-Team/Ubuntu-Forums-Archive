---
title: "GSPCA Webcam Stop Working After Update v4l-dvb-kernel"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by ramadhian on 2008-03-26
I used to get my Lexcron Webcam with GSPCA Driver work very well with Gyachi

but it wont work anymore since I update v4l-dvb-kernel from

 **hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)** 

dmesg output :

[ 7432.820334] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 7433.018108] usb 3-2: configuration #1 chosen from 1 choice
[ 7433.178747] gspca: disagrees about version of symbol video_devdata
[ 7433.178756] gspca: Unknown symbol video_devdata
[ 7433.178954] gspca: disagrees about version of symbol video_unregister_device
[ 7433.178957] gspca: Unknown symbol video_unregister_device
[ 7433.179041] gspca: disagrees about version of symbol video_device_alloc
[ 7433.179043] gspca: Unknown symbol video_device_alloc
[ 7433.179078] gspca: disagrees about version of symbol video_register_device
[ 7433.179080] gspca: Unknown symbol video_register_device
[ 7433.180729] gspca: disagrees about version of symbol video_device_release
[ 7433.180734] gspca: Unknown symbol video_device_release


any hints to fix my webcam back work properly ?:(

---

### Post by loell on 2008-03-26
probably go back to the ubuntu kernel.

---

### Post by ramadhian on 2008-03-27
How ?

> **loell said:**
> probably go back to the ubuntu kernel.

---

