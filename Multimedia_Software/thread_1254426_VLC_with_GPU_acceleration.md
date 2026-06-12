---
title: "VLC with GPU acceleration"
date: 2009-08-31
forum: Multimedia Software
---

### Post by rossmoore on 2009-08-31
Hi,

I'd like to get VLC "just working" with GPU acceleration. I have an Nvidia 8Series GPU, so VDPAU should work.

I've just about managed to get a build of mplayer working with VLC, but frankly I don't like mplayer and I'd rather use VLC.

I've found various cryptic discussions about how to do this (patch this, patch that and just compile and build, for example) - but I'm not quite advanced enough to use those instructions...

So, does anyone know of the whereabouts of a reliable howto? Has anyone successfully done it that would like to help me write one? Or should I just wait until probably the release after the release after Karmic to get this functionality (yawn)?

Thanks

---

### Post by rossmoore on 2009-09-03
Does anyone know of a working PPA for this, or of a sufficiently detailed how-to? Surely someone out there also wants this so they can use VLC to watch 1080p movies without the need for a 3GHz CPU? Noone wanting to use the new ION+Atom platform with Ubuntu and VLC for instance?

---

### Post by Gen2ly on 2009-09-04
I haven't seen it yet rossmore, though I have heard of it being done.  nvidia helped the vdpau patches to mplayer but don't think that vlc is up to this level yet.

---

### Post by rossmoore on 2009-09-08
Thanks, Gen2ly. Guess I'll just wait until I stumble upon a suitable PPA at some point then.

---

### Post by xenogia on 2009-09-09
> **rossmoore said:**
> Thanks, Gen2ly. Guess I'll just wait until I stumble upon a suitable PPA at some point then.

My best bet would be to go to the SMPlayer + MPlayer route honestly.

---

### Post by mc4man on 2009-09-09
I think for the moment ( and maybe a very long moment) that mplayer is your best bet as mentioned.

There is support for vaapi and now an experimental patch for vdpau though for either a 1.1 git version is preferred (or maybe necessary.

I don't have the hardware to support though once karmic releases I'll enable it anyway.
While I could always build a 1.1 on hardy some recent changes have made it difficult if not impossible so aren't bothering anymore.

The other thing to consider is vlc will use avcodec for this so your installed ffmpeg libs are also a factor (both static and shared

For vaapi you'd want to show this ifrom ffmpeg
> Enabled hwaccels:
h263_vaapi		mpeg4_vaapi		wmv3_vaapi
mpeg2_vaapi		vc1_vaapi


For vdpau this
 >  built on Sep  3 2009 12:07:47, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
 D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU


A posting on patch
[http://mailman.videolan.org/pipermail/vlc-devel/2009-August/064220.html](http://mailman.videolan.org/pipermail/vlc-devel/2009-August/064220.html)

A thread with good, bad and obscure info
[http://forum.videolan.org/viewtopic.php?f=13&t=53928&sid=13e4d7bbfa994acb6c68d647247f8d26](http://forum.videolan.org/viewtopic.php?f=13&t=53928&sid=13e4d7bbfa994acb6c68d647247f8d26)

---

### Post by rossmoore on 2009-09-09
Thanks evreryone. I ended up using smplayer route - it's an ok front-end for mplayer. I built mplayer with the relevant flags (oh, where is the link for that? I did it a few weeks ago and can't find it any more), and then followed this thread:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

to get smplayer working with it. Actually, that thread has some info on building the latest version of mplayer that includes the necessary support.

So, I'll use VLC for everything unless it runs out of CPU, then smplayer (which doesn't handle quite so many formats so well, but is pretty good).

---

### Post by djungelmums on 2009-11-03
What about Boxee, its supporting VDPAU.

---

### Post by rossmoore on 2009-11-04
Yes, I've also tried out Boxee recently. I like the idea, but in practice have struggled to get it to perform reliably. I haven't spent that long with it though. Thanks for the suggestion, and others may well find that the easiest answer.

---

