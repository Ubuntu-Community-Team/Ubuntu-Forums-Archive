---
title: "DVI/HDMI output to an HDTV."
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by jeff777 on 2007-12-16
I can't get DVI/HDMI output to my HDTV working correctly under Ubuntu.  Here's the situation.

I have an Nvidia Geforce 6600 and a 42" LCD tv.  The TV brand name is Insignia, which is the Future Shop/BestBuy brand.  I haven't been able to find any decent technical information about it, but it has multiple inputs including VGA and HDMI and it supports 1080p.  The video card has both DVI and VGA output.

I have an ancient VGA cable from the early 90s and a new DVI to HDMI cable.  Under Ubuntu, I am stuck in 720x480 resolution if I use the DVI/HDMI cable.  I troubleshot the problem and the Xorg logs show that the NVidia driver is blocking the higher resolutions.  Fortunately, the VGA cable works fine.  I can get nice looking 1080p output via VGA.   

I had Debian installed for a while, and the DVI/HDMI cable worked better.  I could get nice looking output at 720p, but not 1080p.  I went back to Ubuntu and had to go back to the VGA cable.

I'm satisfied with the vga output for now, but I'd like to figure out why DVI/HDMI doesn't work in Ubuntu.  Has anyone else seen this?  Beyond the Xorg logs in /var/log, is there anywhere else I can look to troublehshoot this?  Perhaps its an issue with the Nvidia driver?

---

### Post by pdaigneault on 2007-12-16
I dont know if this will hep but Video issues may be resolved with this program. This worked for me. See thread below yours.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

