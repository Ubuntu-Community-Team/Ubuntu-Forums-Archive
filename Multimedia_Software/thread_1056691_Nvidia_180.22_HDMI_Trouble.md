---
title: "Nvidia 180.22 HDMI Trouble"
date: 2009-02-01
forum: Multimedia Software
---

### Post by buehldot on 2009-02-01
I have a GeForce 9800 GTX+ card in my desktop running Intrepid. I had been using my AOC 23" LCD TV/monitor as a display via a VGA cable. Using the nVidia 180.11 driver, I got a decent resolution with full 3D support and all the bells and whistles.

I decided to switch from the VGA cable to HMDI in an effort to eek out the full capabilities of the card. As expected, the display was not properly configured with a simple reboot. However, none of the available resolutions or refresh rates resulted in a picture that was usable; most notably, there was significant flickering (which I attribute to a bad refresh rate) and the display area dimensions were larger than the physical dimensions of the screen.

I searched the forums and read all about configuring xorg.conf, xrandr, etc. I attempted to manually add the recommended resolution and refresh rate, but got a blank screen on restart. After a few different resolution attempts, I restored my backed up xorg.conf and tried a different route.

Long story short, I successfully installed the 180.22 drivers instead, allowing the nVidia software to create a new xorg.conf, but got the same results. Again, the display was perfect when using the VGA cable, but had the same issues with HDMI.

I have not been able to find anyone with a similar issue. I believe that the problem is one of three things, and am asking for any guidance as to what I might do. It seems to be either the driver not supporting HDMI fully, the display reporting its resolution, etc., incorrectly, or a fault with my xorg.conf that I don't understand.

Yes, I could just switch back to the VGA, but I'm stubborn and would like to find a fix. Any help is greatly appreciated. Thanks for reading. :)

---

### Post by trindy on 2009-02-24
I have the exact same situation with an ASUS motherboard w/embedded geforce 8300 and a Toshiba 26" TV.  In fact, so exact I thought I was reading my notes from what I tried and etc.  The only thing different, I don't have the flicker problem.

Maybe it's related to the 1080i/720p/720i/480p/480i vs. VGA/SVGA/XGA/WXGA.  According to my TV documentation, my TV supports all of those (and other ones I can remember at the time).  Or maybe something to do with interlacing? 

I also tried messing with (option "TVStandard" "HD 1080i") and (option "UseDisplayDevice" "TV") in /etc/X11/xorg.conf.  These options seemed to have an impact, but I just could't find the right combination.  I also tried adding various mode lines, which I believe might only be used when using SVGA or DVI connections.
  
Troy

---

