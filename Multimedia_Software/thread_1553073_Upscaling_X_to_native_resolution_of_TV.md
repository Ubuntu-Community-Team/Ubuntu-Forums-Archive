---
title: "Upscaling X to native resolution of TV"
date: 2010-08-14
forum: Multimedia Software
---

### Post by RoboJ1M on 2010-08-14
Hi,

I have an AMD/ATI based machine plugged into my TV via HDMI.
It's a 785G based board, making it a Radeon 4200.
The native resolution of the TV is 1920x1080.
I use the open source ati driver in Ubuntu 10.04 and everything works fine.

However, if you run something that drops the resolution down lower, the TV goes out of it's 1:1 pixel mapping mode and into it's overscanning 16:9 mode, thus losing part of the image.

Also, when you go back to 1920x1080, the TV does not go back to 1:1 without me manually switching the TV back.

As as example, I play Return To Castle Wolfenstein and it only works well in 640x480.

What I am interested in doing is doing the upscaling on the PC itself.

So RTCW would render in 640x480 and X would upscale this to 1920x1080 and output that to the screen. Then the TV would stay in "Just Scan" (1:1 mapping) mode rather than defaulting back to 16:9.

Is this possible in any way? Any ideas?

Thanks,

J1M.

---

