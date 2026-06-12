---
title: "Upgraded to 10.10 anyone have problems with nvidia drivers?"
date: 2010-11-11
forum: Multimedia Software
---

### Post by vtrader on 2010-11-11
HI,
So I upgraded to 10.10 from 10.04, and I noticed that the nvidia driver are not working all well as they did before. 
Although I get the nvidia logo when X starts, the 3d part does not work well. For example using mplayer -vo gl does not work anymore. When I type glxinfo I get the x error of failed request badwindow message. More anonyingly flash will crash when going to fullscreen.
The 2d part of the drivers seem fine because xvinfo and -vo xv works fine.

Any ideas, solutions?

Thanks.

---

### Post by mikewhatever on 2010-11-11
I don't know what card model you use, you should probably mention it in one of the next posts. It could be that you are affected by the known bug, mentioned in the [ReleaseNotes]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install"):
> The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974) 

If that's the case, perhaps the bug report comments offer some solution or explanations.

---

