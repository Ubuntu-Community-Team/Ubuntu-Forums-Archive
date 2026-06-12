---
title: "what processor is good and not over kill?"
date: 2010-01-24
forum: Mythbuntu
---

### Post by usererror on 2010-01-24
My current mythtv backend & front end is a Pentium 4 2.8ghz with 3gb RAM.

The majority of my videos are 1GB file size in H.264 / AVC with MPEG-4 AAC audio.  This has never been a problem.  Recently got a video with the same spec, but was 1.4gb in file size and the audio was sllloooow when playing via the front end.

If I played the same 1.4gb file on my Core 2 desktop PC it was perfectly fine.

Worth noting as well that ALL videos that MythVideo reads are NOT stored on the Front/Backend system.  They are on another "file server" connected via NFS which is also a 2.8ghz Pentium 4, but with 1GB RAM.

I will add more ram to the file server, and see if that helps, but I've been running this same exact setup for 3 years now without a hick up.

I'm now wondering if I should combine both the "file server" and the mythtv into one "server" but with a newer processor, ram etc.

Would Core 2 Duo be fine?  Or would you recommend going Core 2 Quad?  Or these new i5 processors?  The Server also runs Apache for a few very lightly visited websites.

I'm not doing any HDTV DVR-ing at the moment, strictly doing analog DVR.  I have read that if I am going to ever do HD DRV-ing with Myth I'm going to need a beefy processor.

Thanks for the hardware tips!

---

### Post by ian dobson on 2010-01-25
Hi,

My frontend box (Underclocked C2D 5200@1.2GHz) can play almost anything that I can throw at it. The most important thing is to get a Nvidia graphic card that supports VDPAU (Hardware acceleration for video playback).

On my frontend (videos are on my backend server) the CPU load is about 10% for MPEG2 files and 10-20% for H264 1080p.

Regards
Ian Dobson

---

### Post by Linuxforall on 2010-01-25
Q6600, best value out there now.

---

### Post by usererror on 2010-01-25
> **Linuxforall said:**
> Q6600, best value out there now.

What is a Q6600, exactly? 

Ian - I'll have to check the process load tonight while playing a 'normal' video that has always worked, and then one the one that is not working correctly.  Forgot to do that.

---

### Post by Caps18 on 2010-01-25
I have an Athlon 1.6Ghz I believe, and it can play 1080i,  but not 1080p.  I am upgrading it this week to an over kill CPU that I was given.  We shall see how that goes.  

I would say the video card has just as much, if not more influene on things.  I am going from an nVidia 6200 to an 8800,  that is built in, so I will see what happens.

---

### Post by LowSky on 2010-01-25
Q6600 is a model of a Intel Core 2 Duo

its clocked at 2.4Ghz I believe. Very nice chip. I think it sold for about $150, but its kinda old and Newegg doesn't sell it anymore.

AMD has been releasing some really nice Quad cores for about $100 that will work just fine too.

It could be the low RAM on the Server, but It can also be the settings on your router giving one machine priority over another. Look into that if you can

---

### Post by usererror on 2010-02-15
Does Ubuntu or mythtv support "multi threading"?  I was told to ask that question, and that would tell me if getting a dual core or quad core is worth it.  If it can't even see more than two processors then I shouldn't get the core 2 quads.

---

### Post by movieman on 2010-02-15
> **usererror said:**
> Does Ubuntu or mythtv support "multi threading"?

Ubuntu does. MythTV doesn't seem to do much in the way of multithreading itself, but the backend does fork off separate processes for things like transcoding or commercial flagging, so those will certainly benefit from more than one core.

At the least, if you're watching one TV show, recording another, transcoding another and commercial-scanning another, you can be using at least four cores.

---

### Post by usererror on 2010-02-15
> **movieman said:**
> Ubuntu does. MythTV doesn't seem to do much in the way of multithreading itself, but the backend does fork off separate processes for things like transcoding or commercial flagging, so those will certainly benefit from more than one core.

At the least, if you're watching one TV show, recording another, transcoding another and commercial-scanning another, you can be using at least four cores.

So a quad core could do me some good. There are times where 2 shows will be recorded at once while I watch another, or watch something in xvid format.

---

