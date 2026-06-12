---
title: "Want to record from desktop"
date: 2010-08-15
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2010-08-15
I want to be able to record from desktop and then edit the video and save it under Linux.

Sounds a simple enough request?
I've found it anything but simple and I need some help please...

After looking at many different apps, I think "gtk record my desktop" is perfect. However, to find a Linux video editor that can:
[LIST]
[*]decode .ogv files (the only output format that record my desktop encodes in)
[*]add basic effects/transitions to
[*]add txt (titles) to
[*]and save as H264 MP4 video
[/LIST]
Is proving near impossible.
The closest I get is OpenShot, but that means having to convert the .ogv file to something OpenShot understands, and this induces noise. PiTiVi would be awesome, if only it supported effects and tiltles (which I hear are coming, but this is something I need sooner rather than later).
LiVES, is in the same camp as PiTiVi - Decent titles don't exist or take ages to configure. Kdenlive is too clunky and uses up too much CPU on my machine.

Does anyone have any suggestions as to where to find a suitable video editor under Linux, or should I resign myself to installing Wine and try Pinnacle Studio?

Any help would be much appreciated!

---

### Post by 0004tom on 2010-08-15
You could compile ffmpeg with x11-grab, and capture to any format you want, including xvid/avi and x264/mkv. There's also xvidcapture which records the desktop to an xvid/avi. Oh and istanbul, never used that one so I can't say what format it saves as.

For editing, you actually have abit more choice. There's kdenlive, openshot or cinelerra. openShot being my choice as it's just simple and easy.

What method are you using to convert the .ogv that gives you noise?

edit, thought I'd link you to an easy guide to compiling ffmpeg and how to use it to capture your desktop.

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and

[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by Baldrick_NZ on 2010-08-16
> **0004tom said:**
> You could compile ffmpeg with x11-grab, and capture to any format you want, including xvid/avi and x264/mkv. There's also xvidcapture which records the desktop to an xvid/avi. Oh and istanbul, never used that one so I can't say what format it saves as.

For editing, you actually have abit more choice. There's kdenlive, openshot or cinelerra. openShot being my choice as it's just simple and easy.

What method are you using to convert the .ogv that gives you noise?

edit, thought I'd link you to an easy guide to compiling ffmpeg and how to use it to capture your desktop.

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and

[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

Which is all fine if you have the time to compile endless files. Sorry, if I sound ungrateful for your help. I'm really very thankful.

However, I really just want to install an app (or 2) that will pretty do much what I need 'out of the box'. I really don't want to tire around endless coding just to MAYBE get what I need.

Which is why I offered apps that don't work out of the box in my original post, in the hope that someone may offer me a more suitable alternative.

But, again, thanks for your help which was much appreciated!

---

