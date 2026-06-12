---
title: "totem/VLC dont work"
date: 2009-02-18
forum: Multimedia Software
---

### Post by antn on 2009-02-18
Hey,
I am sorry for my very general problem, but i do not (yet) know how to specify it. I installed Ubuntu a few days ago, and everything's fine, except that i can not play videos. If i try to open an .AVI or .wmv file, both VLC media player and Totem pop up for 1 second and vanish immediately.

I installed the basic packages mentioned in the sticky thread, but i have know idea if that would help to solve my problem anyway.

Thanks a lot in advance!

antn

---

### Post by hello_kitty on 2009-02-18
Try this:

1. Press Alt+F2
2. Type in "gstreamer-properties" and press enter
3. Under the video tab, change the output plugin to "X Window System (No Xv)"
4. Hit the Test button to see if it works.

---

### Post by antn on 2009-02-18
Hey,
Thank you very much for your quick reply.
Now that i followed your instructions, Totem Player Works!
But VLC still just pops up for a second. I would also like to use VLC, do you think I should change some settings especially for VLC (in VLC)?

Thank you!

antn

---

### Post by hello_kitty on 2009-02-18
> **antn said:**
> Hey,
Thank you very much for your quick reply.
Now that i followed your instructions, Totem Player Works!
But VLC still just pops up for a second. I would also like to use VLC, do you think I should change some settings especially for VLC (in VLC)?

Thank you!

antn

Before we go any further, do you have desktop effects enabled?  For me, I can't play games or use VLC player (without flickering video) with desktop effects enabled.  I can, however, use Totem with desktop effects enabled with the fix I initially provided you.  A sort of workaround, if you will.

---

### Post by hello_kitty on 2009-02-18
Also, here is the [LINK]("http://ubuntuforums.org/showthread.php?t=964912&highlight=vlc+stuttering") to the thread that helped me overcome my video problem.

---

### Post by hello_kitty on 2009-02-18
Here are some options you might consider:

1. [Compiz-Switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch") is a program used to toggle between window managers (metacity/compiz) with the click of a mouse.  Not a fix, just a workaround.  This is what I use.

2. Insert *Option "TexturedVideo" "off"* into your */etc/X11/xorg.conf* file under the *driver* option.  This is designed specifically for VLC, mind you.

---

### Post by binbash on 2009-02-18
for flickering you dont need to disable compiz.Just set the video output to x11 at your video player's (vlc) preferences.

---

