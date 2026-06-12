---
title: "logitech camera stops working after a few seconds in some programs or not at all."
date: 2009-12-05
forum: Multimedia Software
---

### Post by brianarb on 2009-12-05
My "logitech 9000" webcam is not displaying video in programs like cheese.

Here's a snippet from the kernel log.
kernel: [ 94.775745] usbcore: registered new interface driver uvcvideo
kernel: [ 95.767214] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
kernel: [ 100.307111] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 100.307123] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 100.307132] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 100.307140] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 124.121327] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 124.121472] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 124.121598] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 124.121730] uvcvideo: Failed to resubmit video URB (-45).
kernel: [ 175.785163] uvcvideo: Failed to query (135) UVC control 2 (unit 2) : -110 (exp. 2).
kernel: [ 218.526148] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).

after the video stops working I can sometimes get it to work again until the next error.
by unplugging the camera, unloading the uvcvideo module and loading it again. by
modprobe -r uvcvideo && modprobe uvcvideo

---

