---
title: "Need some advise on problems with my webcam feed"
date: 2011-02-25
forum: Multimedia Software
---

### Post by blenderfox on 2011-02-25
I need some help on some bizarre (and somewhat annoying) behaviour I'm having with my webcam.

I have three different webcams. All Logitech. Two are "cheapo" ones, and one is a more expensive, HD one.

I'm running the stock Maverick desktop install, with no specifical extras for the video or the like.

I plug in the webcam (doesn't matter which one I use) and it is picked up and can be used. Not a problem, but when I view the feed, the its laggy and choppy. If I plug in the cam onto my Windows XP or Window 7 installs (on the same laptop), the feed is smooth and has no issues. So I figure it has to be something to do with my settings or configurations. Problem is, I can't seem to find out what I need to tweak to smoothen or improve the feed. I've tried reducing the resolution of the feed to the minimum, but that hasn't helped.

Just to give you an idea of what I'm talking about. If I film myself typing at my laptop keyboard, I can see my hands move around the keyboard when I view the footage in Windows, but when I film it in Ubuntu, it's very jumpy, and my hands seem to jump about all over the keyboard -- almost as if something can't keep up.:confused:

Any advice would be great -- this thing has been bugging me for a while, and I would like to get it fixed somehow.

---

### Post by blenderfox on 2011-02-27
Oh, so I'm the only one to have this problem? Great(!)

---

### Post by no2498 on 2011-02-27
see if this helps its frome cheese's help file FAQ'S


The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by blenderfox on 2011-02-27
> **no2498 said:**
> see if this helps its frome cheese's help file FAQ'S


The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.


Thanks for that. I've tried changing the default output and input to various options, including with/without Xv, but, unfortunately, it didn't make any difference. >_<

---

### Post by no2498 on 2011-02-27
you may need to restart the computer to see it work

---

### Post by blenderfox on 2011-02-27
> **no2498 said:**
> you may need to restart the computer to see it work

Tried that. At the moment, I currently have this under the Video tab:

Default Output:
Plugin: X Windows System (X11/XShm/Xv)
Device: Default
Pipeline: xvimagesink (greyed)

Default Input:
Plugin: Video for Linux 2 (v4l2)
Device: None (greyed)
Pipeline: v4l2src (greyed)

---

### Post by no2498 on 2011-02-28
did you click the bottom test button to see if the cam worked before you restarted

---

### Post by blenderfox on 2011-02-28
Yes, both before and after rebooting.

---

### Post by blenderfox on 2011-03-01
Further update on this. I tried using Unetbootin to try out some other distros, and so far, the same behaviour. Tried Puppy and Lighthouse Puppy.

I tried updating Ubuntu to the "studio" version, and I found something. It looks like, for whatever reason, my install is only seeing one framerate -- 1 fps, which is why I'm getting a jerky feed. Attached a screenshot.

[[IMG]http://a.yfrog.com/img610/4886/eu6.th.png[/IMG]](http://yfrog.com/gyeu6p)

So, question is, how can I correct the fps?

---

### Post by blenderfox on 2011-05-04
Closing this thread -- lack of response.

---

