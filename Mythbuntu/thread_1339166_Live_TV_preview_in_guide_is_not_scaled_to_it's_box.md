---
title: "Live TV preview in guide is not scaled to it's box, shows through EPG"
date: 2009-11-27
forum: Mythbuntu
---

### Post by SiHa on 2009-11-27
I noticed from my first install of 9.10beta that the LiveTV preview that displays in the EPG is not scaled to the preview window. It is, instead, as if the EPG is merely overlaid over the TV picture, with a transparent window where a small part of it shows through. 

Now I'm using the 9.10 final release, no updates, and the default Mythbuntu theme.

At first, this didn't particularly bother me. But. I have since had to disable the X Composite Extension (from MythTV/VDPAU wiki)```
sudo nvidia-xconfig --no-composite
``` to stop tearing.

Now in the EPG, I get a strange affect where, as well as the portion that is visible through the window, I also have a random pattern of transparent pixels distributed across the whole guide. The only parts where the TV picture doesn't show through are the coloured bars of the guide.

OK, this isn't a show-stopper, merely a bit annoying, but if anyone knows how to properly resize the preview window, or restore the EPG background to true blackness (or grey diagonalness), I'd be grateful.

Cheers,

Simon

---

### Post by lastdeadmouse on 2011-02-24
I'm having the exact same issue whenever VDPAU is enabled on my new build, but I'm running 10.10, 2.6.37, .24, and latest nvidia drivers.  It's not that I don't have enough CPU (Athlon 2 X3) to do without VDPAU, but it's annoying b/c I bought a GeForce 210 for just that reason.  It is most noticeable and annoying with the mythbuntu theme.  I don't think it's limited to a specific version of anything, unless you're running any of the same versions as me?

---

