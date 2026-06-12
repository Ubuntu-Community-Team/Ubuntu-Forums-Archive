---
title: "ATI x1650 poor GLXgears frame rate"
date: 2011-07-26
forum: Multimedia Software
---

### Post by thegasgranny on 2011-07-26
11.04 x86
4Gb RAM
Dual 2.8 AMD
ATI x1650 radeon (512mb)

Hello,

I've been struggling with this for months now and I've tried some many things, I've forgotten half of them!

Basically, 11.04 picks up my card fine using the open xorg driver. I've got compize desktop effects (wobbly windows) but I can't play any HD video as it stutters and is completely unwatchable.

So to do any video editing, I have to boot into my Windows 7 install where the performance is considerably better.

Now then, I once managed to get a glxgears frame rate of 11,000 before I broke my install and had to re-install. Now I can't get above 300fps

rb@ub:~/Desktop$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.258 FPS
301 frames in 5.0 seconds = 60.023 FPS
301 frames in 5.0 seconds = 60.019 FPS
301 frames in 5.0 seconds = 60.022 FPS

Can anyone help?

Cheers.

TGG.

---

### Post by RagingOcelot on 2011-07-28
I too have the same issue. Overall ATI performance with the Catalyst driver is poor. I can't seem to figure out why, either. I have verified that I've installed Catalyst correctly, too.

---

### Post by needastick on 2011-07-29
Hello,
       I have experienced similar problems and found that the only way I could play HD video on my modest set up was to turn off desktop effects completely.
       I tried upgrading my graphics card which improved things but not completely. glxgears is running at 54000 on my box.
       My next move will be to try squareplayer but I'm nervous of making things worse and not being able to revert back.
                                          cheers, Tony.

---

