---
title: "Playback distortion / stutter"
date: 2010-07-16
forum: Mythbuntu
---

### Post by wildcard442 on 2010-07-16
I am running a fresh install of mythbuntu 10.02 and when I play back some movies (720p, H.264, 5444kbps Bit Rate) I get "distortion".  Typically what would happen is that after a scene / camera anger change, the new frames will still have older frames colors.  Then it will correct itself until the next camera change.  Sometimes a future frame will get displayed as well.  It doesn't really "stutter" other than these "time warps".  Seems like it might be a key frame issue?  Some movies that are the same size and rates will work fine.  

Could it be the movie or maybe my hardware?

I am using a AMD X2 3800+ (2.0 GHz Dual Core 64-bit), 1 GB ram, 40 Gig hard drive, 7900 GT 512 MB video card

Any ideas?

---

### Post by LowSky on 2010-07-16
7900GT doesn't support VDPAU, so it has some issues with HD video. If you can get a newer card, like the GT240 or better it will give you much better video and you can the use VDPAU to take the load off your CPU. Also a 40GB hard drive isn't much space for HD video. 1 hour of HD video can take up over 4GB of space.

---

### Post by wildcard442 on 2010-07-16
ya, I have a 2TB Samba server that I play my videos from.  GigE connection.  I've tried over the network and locally, same issue so it's not the network.

Do those symptoms seem like hardware issue? I guess i should run top and see what my load is at while I play something back.

---

### Post by LowSky on 2010-07-16
Well if your playing an HD video and your processor is spiking, then a VDPAU capable nvidia graphics card can help reduce the load.

---

