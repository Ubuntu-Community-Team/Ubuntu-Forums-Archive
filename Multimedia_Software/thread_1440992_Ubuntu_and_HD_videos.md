---
title: "Ubuntu and HD videos"
date: 2010-03-28
forum: Multimedia Software
---

### Post by schifazl on 2010-03-28
Hello world! This is my first post here so... hello to everyone! :popcorn:

Let me explain my issue... I'm using Kubuntu for a couple of months and I'm very happy with it (almost totally replaced Windows ;) ). Now I'm building a NAS/HTPC with Ubuntu (I think that once I finish testing everything I'll put Boxee on it).

For the NAS questions I'll open another topic :D

Now the HTPC part: I've installed Ubuntu and found that Youtube eats a LOT of cpu time. I have a Point of View POV/ION330-1 motherboard with a dual core 1,6GHz Atom processor and top says this about the processor usage:
360p: 150-160%
480p: 170-180%
720p: 280-290%

Note that I've already searched the entire forum + googled a lot in the past days and I've done some improvements: installed the last flash beta, installed the latest Nvidia drivers, uninstalled pulseaudio and did some minor configuration changes. Before these improvements the HD videos on youtube were simply unwatchable, I got one frame every few seconds, now I have 5-10 fps.

I know that flash is a delicate issue in linux, so I tested some HD trailers in .mp4 and .mov formats with VLC. The results are:
MP4 720p: First few seconds are smooth, but after that the video freezes for about 20 seconds, is smooth again for a couple for seconds, freezes again for 20 seconds and so on. CPU usage is between 120 and 130% (top command).
MOV 720p: The video is really smooth and the quality is high, but every 15-20-30 seconds it freezes for a moment and when it resumes I see huge artifacts for some seconds. CPU usage goes from 30 to 110% (top command).
MOV 1080p: The video is almost constantly freezed, from time to time 2-3 seconds are smooth, but then the video freezes again for 30-40 seconds. CPU usage is almost constantly at 110% (top command).

But... I've saw a lot of people with these specs that runs HD videos (both on youtube and normal HD files) flawlessly. I'm sorry that I'm asking the same question again, but I didn't really found anything else that could help me.

I would really appreciate any help or hint :)

Thank you!

---

### Post by schifazl on 2010-03-28
Well... I'm stupid!

It was enough to run mplayer with the VDPAU option!

Now I have to understand how to do this automatically, without the need to explicitly run it each time.

The Youtube issue is obviously still open :)

---

