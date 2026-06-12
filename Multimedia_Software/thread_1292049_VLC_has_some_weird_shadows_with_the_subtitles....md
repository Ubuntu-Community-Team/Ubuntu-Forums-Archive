---
title: "VLC has some weird shadows with the subtitles...?"
date: 2009-10-15
forum: Multimedia Software
---

### Post by ACLBandit on 2009-10-15
I'm running Ubuntu 9.04 64-bit and VLC 1.02-git Goldeneye.

When I play videos using XVideo or X11 video, the subtitles on any softsub file look as follows: 
[IMG]http://i530.photobucket.com/albums/dd344/aclbandit/Screenshot-1-1.png[/IMG]

There's a weird green-ish shadow behind them that really annoys me.

Running VLC in OpenGL mode, these shadows go away completely (but, of course, OpenGL VLC doesn't let you access the slider bar thing from fullscreen, and has tearing problems with Compiz-Fusion, among other issues). So using OpenGL VLC is not okay at all. (If getting that menu onscreen and fixing the tearing is possible, though, I'll be glad to switch to GL to avoid the subtitle shadows). 

I'd like to know how to fix the subtitles somehow. I need to make that shadowing go away.


I'm sorry if this has been answered somewhere else, but I can't find a solution anywhere...

EDIT: Really weird workaround (which isn't good enough for me): if I change the video mode to anything else (ASCII-art, GL, etc), press stop, play the video some, press stop, and then change it back to XVideo or X11, the shadowing is gone; however, it comes back any time I start the program again.
A possible workaround that could do it for me: some script that I could run which would start vlc, change video mode, stop, then change video mode back to Xvideo and play it would work, so long as I could make it "seamless" (in other words, I can click a video and it *appears* to "just go.")


EDIT2: Aha. Disabling "sync to VBlank" in compiz-settings but leaving it enabled in the nvidia-settings fixes screen tearing in OpenGL mode. Therefore, if anyone can tell me how to show the controller thing in fullscreen OpenGL VLC, I'll call it "solved."

---

