---
title: "ATI + compiz = black videos"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by Catalyst2Death on 2008-03-19
Hello,

After much wrestling and gnashing of teeth, I have the fglrx ati driver working on my desktop and laptop (the desktop is a radeon 9600xt and the laptop is a mobile x1050 if memory serves)

Anyway, I can finally enjoy the benefit of direct rendering, however it seems that fate is not on my side... I can not enable desktop effects, well I can, and they work beautifully, but when I play videos, the video is just a black screen, audio works fine, and occasionally, a frame or two of the video flickers through (usually when I resize it)   this happens on both computers.  Enabling compiz also kills direct rendering, but that is a bug I'm aware of, I just can't find anything about funky video playback...

---

### Post by aashay on 2008-03-19
run "gstreamer-properties" Under Video-Input try changing the plugin to "X window system No Xv". This will work for totem. For vlc, goto Settings->Preferences->Video->O/p modules Make sure Advanced options underneath is ticked. Select the "X11video output"

---

### Post by Catalyst2Death on 2008-03-19
That worked wonderfully!! Thanks!

---

### Post by timcredible on 2008-05-30
worked for me too, thanks!.  i was wondering, what do i set things to for mplayer to work?

---

### Post by elustran on 2008-06-02
I usually have problems with video not being anti-aliased when I use X11 video output.  Have you experienced that, and, if so, found a way to solve it?

---

### Post by bgjmo on 2008-06-18
> **aashay said:**
> run "gstreamer-properties" Under Video-Input try changing the plugin to "X window system No Xv". This will work for totem. For vlc, goto Settings->Preferences->Video->O/p modules Make sure Advanced options underneath is ticked. Select the "X11video output"

im having trouble finding the o/p modules selection.  im sure its there and im just blind but i do not see it.  id really like to fix this problem.

---

