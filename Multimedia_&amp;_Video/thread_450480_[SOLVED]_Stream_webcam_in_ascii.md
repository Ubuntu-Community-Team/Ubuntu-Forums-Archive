---
title: "[SOLVED] Stream webcam in ascii"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by Megaqwerty on 2007-05-21
Is there a way I could stream my webcam in ascii over telnet or something like it? (I'm trying to do this over a very low bandwidth connection (slower than dial-up usually ~30kbps)) which is why I would prefer ascii. Possibly using vlc somehow? Anyway, it would be interesting if anyone here could figure it out.

Thanks in advance,

Megaqwerty

---

### Post by psmar on 2007-05-21
Awsome concept. I am hoping that someone out there has an idea to implement it .
I do hope this thread grows    

pat

---

### Post by reclusivemonkey on 2007-05-21
Well today I get to make two people happy with one reply =]

[http://ascii.dyne.org/](http://ascii.dyne.org/)

Its in the repos; hasciicam.

---

### Post by Megaqwerty on 2007-05-21
> **reclusivemonkey said:**
> Well today I get to make two people happy with one reply =]

[http://ascii.dyne.org/](http://ascii.dyne.org/)

Its in the repos; hasciicam.

Do you know if it will work without a TV Card?

---

### Post by reclusivemonkey on 2007-05-22
Yeah it will work with any v4l device (which webcams are). I'm not quite sure why they word it that way on the site. I tried it a while back and it worked fine with my webcam.

---

### Post by Megaqwerty on 2007-05-22
Sweet, thanks!

---

### Post by Hiperi0n on 2008-02-14
Hi. I have been trying hasciicam but I can't manage to make it work. I get the following error:

Device detected is /dev/video0
Logitech QuickCam Zoom
1 channels detected
max size w[640] h[480] - min size w[160] h[120]
Video capabilities:
VID_TYPE_CAPTURE          can capture to memory
VIDEO_PALETTE_GREY        device is able to grab greyscale frames
memory map of 2 frames: 925696 bytes
Offset of frame 0: 0
Offset of frame 1: 462848
error in ioctl VIDIOCMCAPTURE: Invalid argument - (h)ascii size is 80x40
using LIVE mode

error in ioctl VIDIOCSYNC: : Invalid argument

(the last error repeats indefinitely)

I have an usb quickam zoom and camorama and other webcam programs work perfectly. I have tried all of the commands but doesn't work, live, html or any of the modes. I can't find any solution in internet...
Thanks

---

### Post by Megaqwerty on 2008-02-14
You should probably try starting a new thread, as:
A) I haven't actually gotten around to trying this out yet (believe it or not) so I'm clueless as to what would need to be done to fix this, and,
B) This thread is marked as solved, so I doubt anyone other than people looking for how to accomplish streaming a webcam in ascii will look in here.

Good Luck,

Megaqwerty

---

### Post by Hiperi0n on 2008-02-14
Thanks megaqwerty, I just thought here would be the best place to post my problem.

---

