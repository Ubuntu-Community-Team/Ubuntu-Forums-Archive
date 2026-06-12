---
title: "No video with dual monitors (work around exists)"
date: 2010-02-10
forum: Multimedia Software
---

### Post by raghu1111 on 2010-02-10
I am using ATI binary drivers (but mostly not ATI specific). 

The problem :
when I play a video file on totem or vlc, the video is blank (audio is fine). 

Fortunately I found a workaround at [http://www.fordnox.com/blog/2009/12/no-video-ubuntu-dual-monitor/](http://www.fordnox.com/blog/2009/12/no-video-ubuntu-dual-monitor/) . In gstreamer-properties change video output from "autodetect" to "X Window System (No Xv)". This works for totem. For vlc I have to go to video preferences to select "X11" for video. 

What could be going on wrong? Is there something I can to fix this so that autodetection works? Not sure if this is dual monitor specific or not.

Set up : Lenevo notebook with ATI 3400, connected external monitor through DVI.

---

### Post by raghu1111 on 2010-02-11
bump, before this dies.

Any idea why video does not work anything other than X11? It is mostly ATI driver related and not related dual monitors.

---

### Post by JakartaDean on 2010-04-04
> **raghu1111 said:**
> bump, before this dies.

Any idea why video does not work anything other than X11? It is mostly ATI driver related and not related dual monitors.

It only emerged for me when I plugged in a second monitor.  I can confirm that the workaround worked.  I'm using 10.04 latest beta on an EeePC 900 with Intel 915 module installed.  Everything else works fine.

---

### Post by insm0d on 2010-08-17
Intel driver here and I have the same problem.

I'll see if the workaround works.

---

### Post by completeidiot on 2010-08-20
running unr on eepc 1005ha. 
same problem. 
work around successful.

Thanks!

---

### Post by douceka on 2010-11-02
Works great, thanks a lot!

---

### Post by ScrewUBill on 2011-03-04
I just tried this work around, it works great, thank you for the link.

---

### Post by pingvin on 2011-12-09
Try placing the displays one on top of the other, rather than next to each other. That way you should be able to stay within Compiz's 2048x2048 virtual display max. resolution. Just literally drag them to re-arrange in Gnome's 'monitor' app.

Hope that helps.
Mike

---

