---
title: "Video plays too fast"
date: 2014-02-01
forum: Multimedia Software
---

### Post by rumpus2 on 2014-02-01
I am a first time Ubuntu user.


I have searched through the forums and found many offered solutions but none seem to fix my issue.


Issue: videos play too fast (2-4x normal speed). Local videos and online all play very, very quickly. When I play them with VLC the speed is normal. However, since I would like to use this system as a HTPC with XBMC, the issue with the default video player is a roadblock.

Running 13.10 with all updates.

Current Hardware:
-Intel® Core™2 Duo CPU E7300 @ 2.66GHz × 2 
-4 gb RAM
-lspci | grep ATI generates the following:
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 XT [Radeon HD 4670]
04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]

---

### Post by normcross on 2014-02-07
Hi,
I am now having this problem as well. Started two days ago using 12.04 (AMD/ATI). I did carry out a small update the day before but didn't pay too much attention to what they were. Darn it. 

All videos on disk or net run really fast, with video output jumping through a few random frames and then locks up.

Tried VLC and they did play but still slightly fast with no audio.

Anyone else with this problem?

Cheers.

---

### Post by normcross on 2014-02-08
I  solved my problem by downgrading a recent update of 'fglrx' and 'fglrx-amdcccle' to an earlier version, rebooted and my video was up and running again. Back to Kdenlive and my editing.

Of course it's not ideal but at least it's all working. Keeping a closer eye on the updates for a while

---

