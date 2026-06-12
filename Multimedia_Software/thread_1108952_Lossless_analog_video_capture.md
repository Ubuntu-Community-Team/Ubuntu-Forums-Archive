---
title: "Lossless analog video capture"
date: 2009-03-28
forum: Multimedia Software
---

### Post by DaveM59 on 2009-03-28
Linux newbie here.

Trying to make the move to Ubuntu, I can do almost everything I want to with it -except- make dvds from analog sources.  

Here's how I do it in WinXP:

Guess I should mention first that I'm in the NTSC part of the world.  Capture analog video stream either from VCR or Motorola cable box/dvr using my KWorld V-Stream 883 PCI capture card.  (Conexant 2388x chipset) I use a simple freeware program called VirtualVCR, capture at 720x480 YUY2 lossless compression (Huffyuv codec).  Then use Ulead DVD Movie Factory to edit the resulting (huge) file, and transcode to mpeg2.  Usually I go with a high constant bitrate and break the video into one-hour chunks to record on multiple disks. 2-pass vbr transcoding takes a long time on my old machine, so I only use that when there's an excellent reason to put a long video on a single disk.

This is clunky but I have tried many other systems, and none delivers satisfactory video quality.  Also there are never any problems with audio sync.

The hold-up with linux seems to be in the first step.  All the capture software seems to be limited in various ways, and most want to encode straight to mpeg2, which simply doesn't work on my computer -- dropped frames, artifacts, yecch.  Also from everything I have read, it's best to edit before transcoding.

So the question is -- can that first step, capturing analog video to lossless digital, be done in Linux?  Or am I doomed to dual-boot?

---

### Post by DaveM59 on 2009-04-03
After six days of searches and experimentation I have concluded that the answer is no.

The only tool I found that would support lossless capture using my video capture card and line-in audio input was mencoder.

I tried others, but mencoder was the only tool that I was able to get audio to work in.

Unfortunately there was a lot of video frame skipping, enough so that even on my one-minute test clips, the sound went out of sync.  I believe that mencoder is simply not optimized for this job.  

The simple capture tool I mentioned in my previous post (VirtualVCR) drops very few frames, and also has a special filter that keeps the audio in sync even if frames are dropped.  It is free and open source, but Windows-only  -- it is designed to work with WDM drivers.

Looks like I'll be keeping my XP partition.

---

### Post by spotteddog on 2009-06-09
> **DaveM59 said:**
> After six days of searches and experimentation I have concluded that the answer is no.

The only tool I found that would support lossless capture using my video capture card and line-in audio input was mencoder.

I tried others, but mencoder was the only tool that I was able to get audio to work in.

Unfortunately there was a lot of video frame skipping, enough so that even on my one-minute test clips, the sound went out of sync.  I believe that mencoder is simply not optimized for this job.  

The simple capture tool I mentioned in my previous post (VirtualVCR) drops very few frames, and also has a special filter that keeps the audio in sync even if frames are dropped.  It is free and open source, but Windows-only  -- it is designed to work with WDM drivers.

Looks like I'll be keeping my XP partition.
I have tried several versions of Ubuntu over the last few years. Since trying Windows 7rc (What a disappointment! It's really Vista SP3), I have gotten serious about making the change to Ubuntu. For me, if I have to dual boot for a few irreplacable apps, I'll just keep Windows.
Anyway, I have been running Ubuntu 9.04 for a while now and have replaced almost all of my windows apps to my satisfaction. But there always seems to be a road block.

The one thing is capturing analog video, editing and burning to DVD. I only do a few each year, but when I need it, I need it.
I've done a search on the matter and haven't found a solution on this forum.

Just wondering DaveM59, I have you found any solutions since your last post.

Thanks

---

### Post by DaveM59 on 2009-06-10
Hi there, sorry to say the answer is no. 

I see your point about dual boot but I prefer Ubuntu for daily use.  It's faster on older hardware and no hassles with antivirus/antispyware apps.

---

### Post by spotteddog on 2009-06-10
Thanks Dave,

I'll have to re-think this. I'm running Vista on one PC and Ubuntu on an old PC. Still don't like the idea of dual boot, even though I have done it many times.

Spot

---

