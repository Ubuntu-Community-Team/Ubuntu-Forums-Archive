---
title: "Intel Mobile 915GM/GMS/910GML choppy video playback"
date: 2011-05-17
forum: Multimedia Software
---

### Post by CFet on 2011-05-17
Hi all,
I have ubuntu 10.04 on an acer aspire with the Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller. 

According to glxinfo | grep direct, direct rendering is enabled.

I'm trying to watch some anime films in .mkv format. I have tried vlc and the stock ubuntu player. The video is choppy with lag between audio and video. 

Any ideas as to how I can diagnose the problem?

---

### Post by CFet on 2011-06-27
Bump bump, been using a different computer but now back to this one with the same issues. Any help?
Cheers~

---

### Post by BicyclerBoy on 2011-06-27
The performance you have maybe all the intel graphics can deliver.

The 915GM uses the GMA900.
The GMA900 & 950 can not really do anything to help video decode. It might be able to help partially decode mpeg2 video (DVD) playback.

What is your CPU ?
Because your CPU is doing all the work..
The video encoding used in the file may have a big impact on performance.

As a general metric..(H264 std broadcast not bluray rips)
a GMA950 (945GME chipset) with an atom just manages mpeg4/10 H264 576i.
This was using i915 driver from xorg-edgers ppa. The std package was not usable.

A core2duo runs about 50% decoding H264 1080i, so has no problem with mpeg2.

Video encoded with more basic codecs are easier to decode but have higher data rates & lower picture quality.

mediainfo "filename"
or
ffmpeg -i "filename"
or use VLC & check the media/codecs window/tab..

The .mkv only confirms the container (the best foss).
The contents can be anything.
AFAIK Anime has very high saturation & contrast (CGI) but also with areas of uniform colour. I'm sure this effects encode/decode somehow..

---

