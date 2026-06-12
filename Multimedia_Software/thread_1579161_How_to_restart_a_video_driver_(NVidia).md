---
title: "How to restart a video driver (NVidia)"
date: 2010-09-21
forum: Multimedia Software
---

### Post by Vetal_ca on 2010-09-21
I'm using my Ubuntu 10.04 as a server, headless or with HDMI receiver/TV setup. There is a lot's of topics how to make it work headless/VNS. I found the least trouble is to make a fake VGA from old VGA cable and 3 resistors. 

However, when I start my Ubuntu with Fake VGA it won't switch to HDMI when I turn my Receiver/HDMI on. If I restart X it is fastest way to pick the HDMI Video/7.1 Audio up. I can do it via VNC or ssh and going to do it with 'irexec' so my wife will be able to redetect the HDMI and run XBMC with one button click of the remote.

The problem is restarting X kills all my GUI apps (KTorrent, ...). Is there a way to force the video driver to restart or redetect the screens? May be there is another solution?

My Video is GT210, 1920x1080 + 5.1 LPCM, Alsa 1.00.23 + Pulse Audio

Thanks

---

### Post by Vetal_ca on 2010-09-22
Well, nobody to help here.

I found a solution how to fix these headless, VNC or KVM problem altogether. The key is to extract EDId profile when monitor is on and specify it in /etc/X11/xorg.conf:


*Option "CustomEDID" "DFP-1:/root/edid.bin"*, where DFP-1 part can vary

Here is an article:

[http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/](http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/)

Just make sure to apply the mentioned sequence as a last step. E.g. if you run stuff like this:

[http://forum.xbmc.org/showthread.php?t=70068](http://forum.xbmc.org/showthread.php?t=70068)

Settings must be reapplied.

I tried, everything works fine as if my HDMI display & receiver were on. Proper resolution, refresh rate and surround LPCM sound via HDMI. VNC works perfect

---

