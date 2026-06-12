---
title: "Deinterlacing video"
date: 2008-01-03
forum: Mythbuntu
---

### Post by peely on 2008-01-03
Hi,

I installed MythBuntu i386 a few days ago and pretty much got everything set up after a bit of bashing around (getting ac3 output working, Dvico drivers etc) thanks to the information from various contributors on this forum, thanks!

I've now reinstalled with the x64 version of MythBuntu 7.10 to get every last bit of poke from my Core2 Duo E6700 processor.

Just about everything is fine, with the exception of deinterlacing of films & DVDs.

I have checked the deinterlacing option in the TV Playback settings and this works fine, but I just can't seem to get deinterlacing to work in mplayer. I have tried various -vf pp= options in the Player Settings option, just after the mplayer command but none of them work, I have tried putting the option at various other points too. All this worked fine in the i386 build but not the x64 build.

I'm using an Asus P5K-VM Motherboard, which uses the Intel G33 onboard graphocs controller which I don't believe supports xvmc, or at least mplayer won't start with the option enabled.

Currently, everything except the TV Card drivers are "Stock" MythBuntu following an update, I haven't recompiled anything. Do I need to recompile myplayer, especially to enable x64, SSE0-3 & MMX features, or are they enabled in the distro by default? I don't know what I was expecting, but as well as the loss of deinterlacing support, I can't really see any performance improvement in using x64 over i386.


Thanks,


Neil.

---

### Post by MadeR on 2008-01-22
I have just posted a similar topic:
[http://ubuntuforums.org/showthread.php?t=674879](http://ubuntuforums.org/showthread.php?t=674879)

---

### Post by larsolav on 2008-01-22
Sorry, but but I have a newbie question:
The original poster indicated that he first installed the i386 iso, but then reinstalled using the x64 version (I assume that would be the AMD64 Build iso) because he has a Core2 Duo processor.

I installed using the i386 iso and have the Pentium D Smithfield 820 processor and it is a 64-bit processor too. Should I have used the AMD64 iso even though it is a Pentium processor and not an AMD processor? Everything is working great so far, but could it be working better?

If I should have used the AMD64 iso is there a way to install it to my sda1 partition without having to mess with the lvm mounted /var/lib partitions spanning three hard disks (including the hard disk that houses the sda1 partition).

Thanks for your help and comments.

---

