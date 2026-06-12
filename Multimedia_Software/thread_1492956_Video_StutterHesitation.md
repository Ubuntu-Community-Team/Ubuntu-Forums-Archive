---
title: "Video Stutter/Hesitation"
date: 2010-05-25
forum: Multimedia Software
---

### Post by kircher on 2010-05-25
Hi,

I don't know what what I'm experiencing is called, but the best way to describe it is a stutter or hesitation. When I watch videos (any videos - H.264, xvid, divx, mkv, avi etc.) using totem **or** mplayer, I get random pauses or hesitations/stutters. They are less than a second in duration, but highly irritating none-the-less. Sometimes it does it a few times in succession with intervals of a few seconds. It's as if the hard drive isn't streaming the video to the player fast enough, or Transmission or some other hard drive task is being prioritised rather than the video which is absurd, unless the memory buffer is not big enough. I am running Transmission bittorent at the same time, but it is impossible for it to be bottle-necking the hard drive.

I know they are random, and not errors in the video files because I can rewind the video and the stutters don't happen in the same place.

I don't know if this is relevant, but is there some way to increase the memory buffer size of the video players? Or else if that is not relevant to the problem is there another way to fix it?

I am running Ubuntu 10.04 updated. My system is an AMD Phenom II X4 3.0GHz, 4GB dual channel DDR3 RAM, 9800GT NVIDIA graphics with proprietary drivers, 1TB Seagate 7200.12 with separate home partition and NTFS partition dual booted with Windows 7. I also have a 300GB NTFS hard drive for sharing data between Windows and Ubuntu.

I have googled these symptoms and I have come up with no leads. It may be because I don't know what my symptoms are called, if it has a name at all.

Any help is greatly appreciated. Thank You.

[COLOR="RoyalBlue"]**Solved:** I believe I have resolved this issue. The video files I was watching were also being uploaded simultaneously by Transmission bittorent, so both the video player and the bittorent application were trying to access the same data simultaneously. Still, there should be some sort of 'buffer' or something to prevent this from happening. If anyone knows of a way to change these sorts of settings, it would be helpful, but otherwise it's not a big deal[/COLOR]

---

### Post by rob-ward on 2010-05-25
I'm afraid I don't know what is causing your problem however it might be interesting to find out if you had these issues in VLC. If they don't then it is likely an issue associated with Totem/MPlayer, if you do have the issue then it is likely something to do with the system in general. It might just help someone work out what the issue is or at least narrow it down.

---

### Post by kircher on 2010-05-26
Thanks Rob. I'll try VLC and report back here. I didn't think to try it because I don't like using it as much as totem or GNOME mplayer.

---

### Post by hojjan on 2010-06-05
I have the exact same problem (kind of a relief to know someone else does too).

It's especially noticable in videos, but it appears to affect all multimedia (audio, flash video etcetera). I have yet to find any definitive diagnosis, and much less any solution or workaround to this. I have suspected it may have something to do with GNOME or one of its processes, since this does not occur when I run KDE (or anything not dependent on GNOME) and seems to persist with different video drivers. 

My setup is as follows:

780G/SB700 Gigabyte motherboard
AMD Athlon X2 7750
4GB DDR2 RAM 
Radeon 4770
Ubuntu 10.04 amd64

EDIT: Turned out it was a bug with pulse audio. Resolved by removing it.

---

