---
title: "Video Playback"
date: 2009-04-04
forum: Multimedia Software
---

### Post by deboare on 2009-04-04
Hello everyone,
I recently made a step to Ubuntu and I'm trying to figure out to have everything I had on my Windows desktop, well, almost everything. Yesterday I hit the problem when I increased the Visual Effects (System, Preferences, Appearance) in Ubuntu from None to Normal or Extra my Totem Movie Player would flicker all the time.
I solved this problem by changing the video output of gstreamer to "X Window System (No Xv). So by just typing in the terminal: gstreamer-properties and changing this property.
However, when I now watch a movie, some are worse than others, the video just blocks for say half a second (together with the audio, however I don't think this is where the problem lies) and then keeps playing again.
I have no idea where to start googling or looking on to forums for this problem, hence I just made a thread about it.

Thanks
brecht

Edit: my OS is Ubuntu 8.10 x86
Edit: I'm not sure but I think that the problem doesn't happen when not playing full screen. I've been switching back and forth the past couple of minutes and in full screen it happens noticably while in 1x I don't notice a thing.

---

