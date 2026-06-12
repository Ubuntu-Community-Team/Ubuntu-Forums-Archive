---
title: "Brasero doesn't find mplex in 13.04"
date: 2013-05-22
forum: Multimedia Software
---

### Post by Valpskott on 2013-05-22
So, I installed Ubuntu 13.04 32 bit a couple of weeks ago.

Now, when I try to make a video-proejct, I get the error messages that I need to manually install "mplex (GStreamer-plugin)". So, I manually installed it via the software center. Still the same problem, even after a reboot of the computer. The software center says it's installed.

I googled around and someone getting the same error message got the advice to do this:
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

Which I tried, the library installed without any problem, but I still get the message to manually install "mplex (GStreamer-plugin)".
I've also installed:
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
ubuntu-restricted-extras
ffmpeg
mencoder
kdenlive

A clue could be that while I have libx264-123 installed, kdenlive thinks I do not. So it seems like there is some general idiosyncrisity in what Ubuntu knows is installed.

---

### Post by somethingentirelydifferent on 2013-09-05
Same here. 

GG default applications at ubuntu :)

Don't they see this?

[IMG]http://i.imgur.com/MLYSrys.png[/IMG]

2 starts brasero, 5 starts k3b
still brasereo default so many years now..

---

### Post by sabinedoll on 2013-10-11
I had the same problem. I finally found Bombono (in the Ubuntu software center). It automatically transcodes, writes DVD images in PAL or NTSC, and burns them to DVD, and also adds nice menus. No need for Brasero to do this.

---

### Post by Yellow Pasque on 2013-10-11
K3B is great, but it also requires a ton of other KDE stuff (even if installing without 'Recommend" packages). I prefer xfburn.

As for the issue, Brasero now uses gstreamer1.0, and Ubuntu does not build gstreamer1.0-plugins-bad with mplex support (even in latest Saucy/13.10), so the only way around the issue is probably to use a PPA version of gstreamer1.0

```
configure: *** checking feature: mplex ***
configure: *** for plug-ins: mplex ***
checking for MPLEX... no
configure: *** These plugins will not be built: mplex
```

You can try filing a bug request: [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+filebug](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+filebug)

---

### Post by Yellow Pasque on 2013-10-11
I filed a bug for Debian: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=726064](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=726064)

Launchpad/Ubuntu bug: [https://bugs.launchpad.net/bugs/1239029](https://bugs.launchpad.net/bugs/1239029)

---

