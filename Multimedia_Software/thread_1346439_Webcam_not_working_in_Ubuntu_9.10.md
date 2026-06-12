---
title: "Webcam not working in Ubuntu 9.10"
date: 2009-12-05
forum: Multimedia Software
---

### Post by Lyon on 2009-12-05
Originally I thought this was just a problem related to my capture card, but the same thing seems to be happening with my webcam too now.

When I try to stream off of websites like livestream, my webcam has a tendency to either flicker on briefly, or just simply not connect at all.

I tried installing Cheese to see if it would connect to that, but it is just showing the test screen.

My laptop is an HP Pavilion dv6000 with an internal HDA Intel webcam. Fresh install of Karmic Koala and linux kernel version is 2.6.13-15

Hopefully this is enough information to make heads or tails of this

output of lsmod|grep video:

```
Module                  Size  Used by
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
video                  23612  0 
output                  3680  1 video

```

output of dmesg|grep video:

```
[    0.598875] pci 0000:01:00.0: Boot video device
[   12.800533] Linux video capture interface: v2.00
[   12.802907] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   12.814957] usbcore: registered new interface driver uvcvideo

```

Really stumped on this because it looks like everything SHOULD be working fine.

Please help with this, video and sound are always what give me the hardest time in Linux and I can't go back to Windows after all the time I've put into it

EDIT: So this problem seems really inconsistent. When I have livestream studio open, the camera runs and then stops immediately, but holds up the camera as a source it seems, because then Cheese can't access it. However, nothing shows up in dmesg when livestream fails to run the camera. When I close firefox, it frees up the camera and then Cheese can access it again. At least I think that's what's going on. I'd really like to get streaming video working.

---

### Post by bulbmaker on 2010-01-10
..bump..
same with mine(hp pavilion dv 6226tx)
is there any tool to test my web cam whether it is working or not?

---

### Post by no2498 on 2010-01-26
its not just only webcam's
video output is in use by something else
if i try 1 of my videos

to test the web cam
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
get cheese and wxcam
1 will find your cam after this

now i have a ?
on 910 put something red and green in front of your cam
red on the left green on the right
how does it show up ?

---

