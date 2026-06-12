---
title: "Tiny flickers/jumps playing DVDs"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by geppz on 2007-10-27
Hi there, I have a new powerful Dell D830 core2duo with videocard intel X3100 but I get constant flickers or tiny jumps while playing video. Ubuntu Gutsy stable stock kernel, kde and no compiz.

Problem happens at any resolution, even without audio, on Xine, Mplayer, Kaffeine etc, deinterlace disabled. CPU utilization is minimal. It is not a problem of disk-DMA because it also happens if I rewind 10secs and in that case the everything is in cache and the DVD doesn't read. With the RT-kernel the problem is much worse.

I have a DVD with 30fps progressive images (Babylon5 series computergraphics) and there are some uniform camera pans where these tiny jumps can be seen clearly. I'm not sure if the source is at 30fps or 29.97 but it shouldn't matter (0.01% of difference) and both are about an exact divider for the LCD refresh 60fps so jumps should never happen, and they happen even if I force 30fps.

What I see is that about once per second (very regular) there a few frames with flickering or tear artifacts (not sure about the exact type of artifact because it happens very quickly) on the images like if a part of the frame was belonging to the frame before or in some cases even black, and the other half belongs to the new frame.
Playing in slow motion I can confirm that the DVD source is correct, the problem is in the playback and it is also not an interlace problem because there is no interlace in this material.
This would seem like it didn't have a hardware double buffering... seems very strange to me with such a new video chipset. How can I check this?

With the RT kernel the problem is much worse: the artifacts are much more frequent and happen irregularly, and are also bigger like more than 1 frame skipped

From "top" or "htop" no processes appears to use cpu more than 0.1% apart from the obvious dvd player and the X process.

The problem does not happen on another older computer with a Matrox standalone video card, LCD screen and Debian.
This happens also if no audio is specified in mplayer. Mplayer does not declare dropped frames.
Happens with every mplayer video-output which I could test (vx, x11, gl, gl2).

Any idea on how I can investigate further?
Is it a driver problem?

---

