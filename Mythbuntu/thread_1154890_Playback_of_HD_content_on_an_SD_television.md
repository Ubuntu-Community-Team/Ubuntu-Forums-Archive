---
title: "Playback of HD content on an SD television"
date: 2009-05-10
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2009-05-10
I've been trying to research how everything will work together and what I need to consider before setting up my systems. I'm trying to make sure my assumptions on things don't end up costing me time/aggravation/hair-pulling at time of installation.

So, I'm going to have a backend which will record HD content and playback to an HD-capable television. However, one of my frontends will be connected to a SD television. The frontend I put in will certainly be capable of playing back HD television when I eventually replace the SD television.

What is the easiest way to play back the programs recorded in HD on a frontend connected to an SD television? I know I can transcode on the backend, but are there other ways to accomplish this?

---

### Post by 4dognight on 2009-05-10
I have the same scenario as you described.
My HD recordings play back just fine on my 33 in Tube Tv, connected via svideo.
I dont do anything with my HD recordings to play back on it. They just show up in a letterbox format. Not sure if there is anything going on behind the scenes or what. It just works, and thats goo enough for me. :)

---

### Post by mythms on 2009-05-10
I used atv-bootloader to load mythbuntu (8.04) on an AppleTV.  The AppleTV is running as a frontend.  It is connected to a SD television.

---

### Post by newlinux on 2009-05-11
as stated, no transcoding necessary. All content will automatically be scaled down to the resolution of the connection and that the tV is capable of. It will still require an HD capable playback frontend (which you stated you have) because the decoding needs don't change - he HD will just be downscaled through the connection. I do this with one of my old TVs through S-video as well. So you don't have to do anything but get your SD output to your TV working.

---

