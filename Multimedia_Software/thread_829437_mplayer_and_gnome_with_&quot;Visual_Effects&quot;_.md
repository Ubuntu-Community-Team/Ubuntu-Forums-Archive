---
title: "mplayer and gnome with &quot;Visual Effects&quot; set to Normal"
date: 2008-06-14
forum: Multimedia Software
---

### Post by sleepsus on 2008-06-14
Hi,

I just installed Hardy and while playing divx videos in windowed mode using the -vo gl or gl2, mplayer flickers wildly.

This only happens when gnome's Visual Effects is set to Normal or Extra. 
If I set it to None mplayer works perfectly.

Anyone know how these two can play nice?

Thanks. Mark

---

### Post by owbizi on 2008-06-14
Do you use an ATI video card? If yes, which one?

There are well known problems with composite managers (like Compiz) and video playback at the same time with ATI video cards, but it appears to be somewhat fixed on new ones.

---

### Post by sleepsus on 2008-06-15
yes, I'm using an ATI Radeon HD 3200.

Anyone know how fix it?

---

### Post by owbizi on 2008-06-15
You can try this:
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712).

For some people it worked, and for some it didn't. Also, just for knowledge, this bug isn't a driver problem at all, as it seems to happen because of a conflict between render modes (xvideo is used both by compiz and other programs), or something like that. At all, because on nvidia cards, for example, it works normal...

Another method to solve this is to set the video output of mplayer to x11, leaving xvideo just for compiz' use. Other applications, though, will continue flickering, and x11 is a bit more heavy than xvideo to the cpu...

Also, if you leave the "Unredirect fullscreen window" option enabled in compiz general settings, when you play a video on fullscreen mode, it will not flicker. Strange, isn't it? :)

---

