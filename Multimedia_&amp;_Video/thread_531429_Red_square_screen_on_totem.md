---
title: "Red square screen on totem"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by Lex Luthor on 2007-08-21
Hello, friends,

  I was using feisty here at work, so I decided to upgrade to Gutsy.  My totem was working perfectly on both systems.
  But due to some proplems on udev in my gutsy instalation, I decided to downgrade to Feisty again. So I formatted "/" my partition and installed Feisty.  My /home was not changed, I just mounted it again.

  My problem now is that totem is not working anymore. When I oen it, it just starts playing  with a red squared screen. No vídeo, but the sound is OK. I installed the codecs it asked me to. This is the screen:
   
[[IMG]http://img132.imageshack.us/img132/3845/errototemai5.th.png[/img]](http://img132.imageshack.us/my.php?image=errototemai5.png)

  If I open the file on mplayer I can play the movie. I've already erased config files on .gconf and also .gnome2, but nothing changed. 

abraços.....

---

### Post by lereveur on 2008-03-22
Thanks for posting the screen shot. That's the exact same issue I had. I'm not sure whether to call them red squares, red x's, or red diamonds. In any case, I'm assuming you're using totem-gstreamer since that's apparently the default installation.

The problem from what I can determine is that gstreamer isn't able to properly autodetect the appropriate video output plugin to use. If I select "X Window System (No Xv)" or ("X Window System (X11/XShm/Xv)" with device "SIS 315/330 series Video Blitter"), then the video display correctly. Any other choices produces the red squares.

To get to these settings (I'm not sure why Ubuntu isn't installed with this in the menus by default), you can either add "Multimedia Systems Selector" to the menus or type "gstreamer-properties" in terminal. In Multimedia Systems Selector, click on the "Video" tab and then select the plugin that works. There's a "Test" button to verify whether the plugin works.

My guess is that this is an issue with computer motherboards that have the SiS chipset. My motherboard is a FoxConn / WinFast K7S741GX

---

### Post by chiefofthejojos on 2008-04-24
Thanks lereveur, this was bugging me for awhile and your fix worked for me.  Have either of you reported this bug?

---

### Post by lereveur on 2008-05-11
I haven't reported the bug. I'm not even sure where to report it.

---

