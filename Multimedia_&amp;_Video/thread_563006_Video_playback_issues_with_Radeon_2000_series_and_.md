---
title: "Video playback issues with Radeon 2000 series and proprietary driver"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by fa2k on 2007-09-29
Edit: Mostly fixed with the fglrx 8.42.3 drivers. 

--

When playing video on my server/media-PC, I get various quality issues.

The setup is 
AMD Athlon64 3800+ CPU
ATI HD2400 Pro Graphics card
1GB of RAM
fglrx proprietary driver v.8.41.7 for x86_64 (using OS driver limits TV (DVI) to 640x480, which made installation hard, because a  quarter of the wizard was not visible. I should probably file a bug about that).
I downloaded the driver from ati.amd.com

It is not an incredible machine, but I've been able to play back 720p content in H.264 on less powerful hardware. Also, it plays all video fine on Windows (Vista), but Windows is not an option because it also serves as an internet gateway.

When using the Totem player, and VLC with the default video output module, I get tearing of the image in high motion scenes. This applies to both low- and high-resolution content. For lo-def, it is barely watchable, for hi-def, it is also dropping frames like crazy (i.e. "lagging").

I enabled Xvideo with
aticonfig --overlay-type=Xv

When using the Xvideo output module in VLC or MPlayer, I get a distoriton that is kind of hard to explain. There seems to be something wrong with the timing, that frames are presented in the wrong order. One could maybe call it "choppy".

Both glxinfo and xvinfo indicate that the systems are up and running. 

So my question is: Can I expect this to work now? Are other people experiencing this? Is the driver too immature, or am I doing something wrong. 

Also, if there is a work-around, please tell me.

Thanks,
-Marius

---

