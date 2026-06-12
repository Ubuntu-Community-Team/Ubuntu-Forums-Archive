---
title: "Audacious 2 (64-bit) - no SPC playback / crash"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Faolan84 on 2009-10-31
After upgrading Ubuntu one of the first things I did was fired up Audacious and proceeded to attempt to playback the SPC rips that I had playing while I was reading when guess what? I can't get them to play back like they were in the previous version of Audacious. Instead the program pauses for a few seconds and segfaults.

Here is the problem. On 64-bit Linux, Audacious is (or was) the only program that could handle that particular format because it used an internal version of libopenspc rewritten from scratch. On 32-bit Linux this is not a problem because SPC playback is included in GStreamer so Rhythmbox can play it without any problems. The reason this feature isn't implemented in 64-bit Linux is because parts of the original libopenspc are written in 32-bit assembly code. (Hence why Audacious rewrote this code for internal use).

What I want to know, is there something I am doing wrong here, like another input plug-in that is interfering, or is this feature now broken on 64-bit Linux with the transition from Audacious version 1 to Audacious version 2? Also, I would like to know if anyone else has had this particular problem or similar.

Thanks in advance.

---

### Post by Faolan84 on 2009-11-01
Installing the package "xmp-audacious" seems to solve this. I have to give credit to smartboyathome on this one though.

I'm guessing the actual modified library of libopenspc exists in this package or has dependencies that are not specified. If so this is a dependency bug because the SPC plug-in does not specify it needs this package and in enabled in the default audacious package. Also, smartboyathome also informed me that installing this packages fixes other crashes caused by certain formats.

If your experiencing crashing with Audacious, you may want to try this one out.

Source:
[http://www.ostalk.org/showthread.php?tid=663](http://www.ostalk.org/showthread.php?tid=663)

---

