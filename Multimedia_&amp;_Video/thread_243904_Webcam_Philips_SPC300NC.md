---
title: "Webcam Philips SPC300NC"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by freronn on 2006-08-25
Hi,

I simply cannot get my webcam to work.
Reading the homepage of the spca5xx driver, it lists my Philips SPC300NC as one of the supported cams. Good. And I think I have everything needed in my kernel: lsmod gives (contracted)
spca5xx               630928  0
video                  16260  0
usbvideo               27524  0
videodev                9856  2 usbvideo,spca5xx
usbcore               130692  4 usbvideo,spca5xx,uhci_hcd

That seems fine. lsusb:
Bus 001 Device 002: ID 0471:0326 Philips
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

It sees my cam, obviously.

So, there should be a /dev/video0 device. There is not.
I try to make /dev/video0 and /dev/video1 manually, set priorities a+rw, chown to root.video, add myself to the video group. Still when I run xawtv, it says

This is xawtv-3.94, running on Linux/i686 (2.6.15-26-386)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Filen eller katalogen finns inte
v4l2: open /dev/video0: Filen eller katalogen finns inte
v4l: open /dev/video0: Filen eller katalogen finns inte
no video grabber device available

(sorry for the Swedish)

WHAT is wrong?? This drives me crazy....

---

