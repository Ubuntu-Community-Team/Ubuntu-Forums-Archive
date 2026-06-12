---
title: "What's the lowest hardware required to play HD video?"
date: 2009-06-26
forum: Multimedia Software
---

### Post by skullmunky on 2009-06-26
So, totally not an Ubuntu question at all, but bear with me.  I want to make hardware purchasing recommendations to people buying computers for a single purpose, which is playing back HD (1920x1080) video files.  I guess in normal life this would be like a media center application - the specific case I'm interested in is for video projections for artists and designers, where you basically just need to play a single video on a loop.  

This used to be done with VCR's, and then with DVD's, and now in the HD era, people are using whole computers just to do this because, I guess, it's easier than building a blu-ray authoring system.  

I gather that people often buy Mac Mini's to do this, but at the same time the population I'm talking about often don't have a lot of spare cash to throw around on extra computers at $700 or more a pop, and are sort of more in the OLPC budget range.  My gut feeling is that there ought to be a cheaper way to do this for $300 or less, either by building something in a shuttle or set-top box case or by getting whatever's on sale at WalMart.  (Oh, and then putting Ubuntu on it and using either VLC, or MPlayer, or MythTV, or something similar to make a nice little plug-n-play dedicated video player box).  

So the question I have is: how low can you go?  What's the cheapest hardware I can get that'll play HD video?  (For this application, ability to handle great compression is less important - filling up the entire hard drive with a single 2 minute video is perfectly fine).

---

### Post by steefjeqv on 2009-06-27
Hi,

The 2 keywords are Nvidia and VDPAU.
You'll need an Nvidia GPU (or onboard graphics) with at least 512 mb of the 8xxx or 9xxx series.
The Nvidia Ion platform should be ok too.

If you're using an AMD CPU, your best choice is the K-10 series. 
K8 and K9 are also possible but they need a fixed speed between 1800 and 2000 mhz.

The low end cards (x400 and x500) have trouble coping with the highest deinterlacing settings (temporal_spatial) when using Xine. Lowering the deinterlacing to bob or temporal solves this problem.
VDPAU is still (rapidly) in development so this issue could be solved (for instance with more deinterlacing options).

Greetings,
Steven

---

