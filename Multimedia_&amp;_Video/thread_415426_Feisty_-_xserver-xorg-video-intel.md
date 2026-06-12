---
title: "Feisty - xserver-xorg-video-intel"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by John Williams on 2007-04-20
Anyone trying the new xserver-xorg-video-intel driver? I am running a ecs 945G-M3 MB with an onboard intel 82945G/GZ video chipset. Needless to say I am not happy with the resolution options. I want 1152x864.

Tried the i810 generic one with and without 915resolution hacks. :( 

Next, I tried the i810-modesetting version for a while. That was the only one that could get close on 1152x864. xvidtune does not work on my config either. This resolution worked ok on i810-modesetting but had wide bands of 3/4 inch on each side using 1152x864. On past systems, I could tune the modelines with xvidtune...argh. :mad: 

installed xorg-video-intel. re-did the dpkg-reconfigure and told it I wanted the 1152 ones but it still defaults to 5 - 2 low ones, 1024x768, 1280x1024 and 1280x1280. :confused: 

I ran into displayconfig-gtk. It looks interesting, but no info on how to run it...  Anyone tried it?

Lastly this new driver pkg seems to be the long term answer so I think I will keep it installed. 

Any insight would be appreciated.

---

