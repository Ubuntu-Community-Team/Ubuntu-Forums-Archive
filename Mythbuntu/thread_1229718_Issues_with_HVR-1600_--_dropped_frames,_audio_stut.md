---
title: "Issues with HVR-1600 -- dropped frames, audio stutters"
date: 2009-08-02
forum: Mythbuntu
---

### Post by heartburnkid on 2009-08-02
Hi all.  I'm using Mythbuntu 9.04 32-bit on my living room PC, and I'm having a few issues with a new tuner I just installed, a Hauppauge HVR-1600.  I'm using it with a GeForce 6200 video card, and I've implemented the vmalloc fix in menu.lst to get the two working side-by-side, but now I'm seeing a different issue, namely, I'm getting dropped frames and audio stutters when watching live TV.  This seems to be related to the virtual memory issue, as I've noticed the frame drops seem to vary with the value I set vmalloc to; vmalloc = 256M seems to result in the most stable picture (but even then, frames start dropping after about 5 minutes of viewing), while vmalloc = 192M and vmalloc = 512M both seem to drop frames within a minute or two.

Is there a fix I could implement on my current platform for this?  Failing that, would going to 64-bit Mythbuntu solve the problem? (I'd much prefer the former, as I've done a lot of tweaking here, and I'm only using 2.5GB of RAM anyway)

I should note that I'm capturing from DirecTV via S-Video, just in case it makes a difference

---

### Post by heartburnkid on 2009-08-03
Decided to try 64-bit; problem is now even worse.  Same video quality problems, but now Mythfrontend crashes when I try to exit live tv.  On the plus side, I can definitively say the issue isn't with the vmalloc.

Help?

---

