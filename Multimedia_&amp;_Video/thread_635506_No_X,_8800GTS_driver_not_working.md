---
title: "No X, 8800GTS driver not working"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by Nzer24 on 2007-12-08
I'm having a bunch of problems with my video output.

I have a nVidia 8800GTS and I've had it working for a little while now, but it recently had a total driver/X meltdown. I accidentally removed the regular driver (using Envy), and couldn't reinstall it. I used apt to get the "nvidia" driver, because that is what Envy was trying to install, and I enabled it in xorg.conf. Next time I boot up, I get a total blank screen after the splash and loading bar. I go into recovery mode and enable the driver "vesa", which then lets me get some basic video. I try to properly install the nvidia driver via the restricted driver utility, but the next reboot yields the X failure BSOD-thing. I try and go back to vesa, but it totally scrambles my output ( it is warped and dim, btw, I'm using a CRT monitor). Then, to make matters worse, it says my HAL has failed. 

Totally stuck here, but I don't care if I have to reinstall or wipe anything. I'd prefer to save my /home though, and I do have some windows partitions on my computer that I could dump it in for a bit. 

My card's working fine on windows, so it's only a software problem.

I also noticed that the Gutsy LiveCD gives me the same screwed up output as I got before, and it freezes often. I was able to install Ubuntu before when I had a different video card, but I might not be able to get that one back to install again.

---

