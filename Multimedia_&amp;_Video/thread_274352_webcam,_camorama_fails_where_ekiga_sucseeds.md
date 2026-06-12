---
title: "webcam, camorama fails where ekiga sucseeds"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by tsr on 2006-10-09
Hi,

I've got some kind of integrated webcam
```

pisken@gizmo:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0c45:62c0 Microdia
Bus 001 Device 001: ID 0000:0000
```

check [http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html") for reference, search microdia).

It works with ekiga (eg, pressing the video button lights up the cam-light on the screen and ekiga starts showing my beautiful self :grin:)

However with Camorama I get the classic error:
```

Could not connect to video device (dev/video0).
Please check connection.

```

According to the device manager the 
'video4linux.device' is located at /dev/video0
'usbraw.device' is located at /dev/bus/usb/001/002

```

pisken@gizmo:~$ dmesg | grep uvc
[   35.351875] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   35.353439] usbcore: registered new driver uvcvideo
[  797.941171] uvcvideo: Failed to query (1) UVC control 2 (unit 3) : -32.
[  798.210435] uvcvideo: Failed to query (1) UVC control 2 (unit 3) : -32.
[  798.441223] uvcvideo: Failed to query (1) UVC control 2 (unit 3) : -32.
[  799.808575] uvcvideo: Failed to query (1) UVC control 2 (unit 3) : -32.
[  826.634742] uvcvideo: Failed to query (1) UVC control 2 (unit 3) : -32.

```

(I don't know if these last infos are useful, just trying to cram as much maybe useful info here that I can think of, nope I'm not really a power user)

Ok, thanks in advance for your help, much appreciated.

/tsr

---

