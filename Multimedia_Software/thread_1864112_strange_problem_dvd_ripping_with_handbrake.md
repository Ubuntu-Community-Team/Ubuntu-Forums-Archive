---
title: "strange problem dvd ripping with handbrake"
date: 2011-10-18
forum: Multimedia Software
---

### Post by beew on 2011-10-18
Hi,

I have ripped some dvds into .mkvs with handbrake, it all seemed to work well until I play them back. For some strange reasons when I go to full screen in mplayer2 and VLC the videos kind of slow down and freeze, _but playback is fine if I switch from vdpau to xv in mpalyer2 and disable GPU acceleration in vlc_. 

I play full screen videos with vdpau fine on this machine, the only problem I have is with these videos which I ripped from dvds using handbrake, maybe I have gotten some settings wrong? (the dvds themselevs play fine in full screen when mplayer uses vdpau and vlc uses GPU acceleration)

I am on Maverick, Nvidia current 285.05.

Thanks.

---

### Post by beew on 2011-10-19
Tried to rip into .m4v, the same problem. Playback is fine if using xv instead of vdpau, otherwise it freezes after a few minutes.  vdpau in general performs great except for these videos ripped from handbrake. 

I should note that cpu usage remains very low when the videos freeze (~5%) so it has nothing to do with high cpu usage.

Any idea what might be the problem? Thanks.

---

### Post by beew on 2011-10-22
I have done some testing and it seems that the problem only occurs in Maverick but not in Natty (the same machine)

Here is what I found. 

I can play the mkv and m4v files in Natty using vdpau without any pause or freeze  regardless whether I ripped the dvd with handbrake in Natty or Maverick.

Regardless of whether the dvd is ripped with handbrake in Natty or Maverick if I play the m4v or mkv file in Maverick I experience freezing if I use vdpau, using xv it is ok.

I have played many mkv and m4p files in Maverick using vdpau without a problem, but they are not created by handbrake.

What conclusion should I draw? Thanks.

---

### Post by beew on 2011-10-23
Bump!

---

### Post by BicyclerBoy on 2011-10-23
Sounds like the maverick video driver or the VDPAU api has a bug..
Or there is better error handling in later VDPAU..
Maybe the maverick version of HandBrake makes invalid H264 files.

Do you use the std repos handbrake ?

I get it from Mr HandBrake's nightly builds so I have something with up-to-date libdvdnav on 10.04.

There been a heap of recent activity on the mplayer.hu/dvdnav mailing-list..
Some of it due to that stupid Thor movie..

---

### Post by beew on 2011-10-24
I also got handbrake from the nightly build.  

However, even if I rip a dvd in Natty using handbrake, playing back of the file in Maverick still freezes with vdpau, whereas  the ripped file plays perfectly in Natty with vdpau; _also if I rip a dvd in Maverick, the file plays perfectly in Natty with vdpau_, so it seems the problem is unrelated to handbrake or handbrake versions.

 On the other hand I can watch all .mkv and .mp4 files in Maverick using vdpau with no issue, except for the handbrake created , so it seems that Maverick and vdpau are not at fault either. 

I am at a loss to locate where the problem is.

**EDITED:** All my experiments are done on the same machine (different partitions)

---

### Post by beew on 2011-11-17
bump!

---

