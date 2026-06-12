---
title: "problem with my webcam"
date: 2010-10-24
forum: Multimedia Software
---

### Post by manash_a1 on 2010-10-24
hello everyone

i am using ubuntu 10.10


i have got my z-star microelectronics usb 1.1 webcam connected in my pc. when i use camorama or cheese booth, the green indicator of webcam appears but webcam doesnt show any image. when i put it in bright light source, it shows the bright light but it goes dark for normal objects. i am new in ubuntu. i have put the lsusb report as follows

Bus 002 Device 003: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

i have checked the device settings using ekiga and have found that it is using v4l2 platform. what shall i do. if i plug in creative webcam, it responses properly but with z-star webcam it doesnt work. is it the compatibility issue. 

hoping for your kind reply

---

### Post by delogren on 2010-10-24
> **manash_a1 said:**
> hello everyone

i am using ubuntu 10.10


i have got my z-star microelectronics usb 1.1 webcam connected in my pc. when i use camorama or cheese booth, the green indicator of webcam appears but webcam doesnt show any image. when i put it in bright light source, it shows the bright light but it goes dark for normal objects. i am new in ubuntu. i have put the lsusb report as follows

Bus 002 Device 003: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

i have checked the device settings using ekiga and have found that it is using v4l2 platform. what shall i do. if i plug in creative webcam, it responses properly but with z-star webcam it doesnt work. is it the compatibility issue. 

hoping for your kind reply


Have you tried luvcview?
It helped me get my UVC compatible webcam working.  And let me know when an outdated web cam didn't.

--del

---

### Post by manash_a1 on 2010-10-24
I GOT THIS MESSAGE AFTER RUNNING LUVCVIEW

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal
manash@manash-G31T-M7:~$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal


WHAT SHALL I DO NEXT

---

### Post by manash_a1 on 2010-10-24
hi there

thanks for the suggestion, well i entered in guvcview and there i turned of no fliker in the settings menu to 50 hz and the webcam works perfectly

---

