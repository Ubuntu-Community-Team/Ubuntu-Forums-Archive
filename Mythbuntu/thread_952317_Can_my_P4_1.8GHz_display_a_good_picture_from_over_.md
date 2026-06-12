---
title: "Can my P4 1.8GHz display a good picture from over the air digital video?"
date: 2008-10-19
forum: Mythbuntu
---

### Post by bglaze1 on 2008-10-19
What kind of playback can I possibly handle with a P4 1.8GHz processor, NVIDIA GeForce FX5200 AGP card with 256MB DDR, and 2GB RAM?  
I know that it can't handle HD.  But I am confused as to whether this means I can't receive over the air digital signals at all, or just HD channels?  I thought over the air digital was different from HD.  Am I right? What is the difference between the two?
The way I understand it, when my video capture card is receiving the video from the antenna in my attic, it will just record it off to a file.  And the problem comes when my processor doesn't have enough power to convert it to whatever resolution I need to display it properly.  I don't have an HDTV, just a regular old 27" tube, if that helps you to know what resolution I would need to display the video.  So I don't need it to look 1080p (obviously), just regular SD would be fine.  Can my computer even handle this, or is it just too old to even possibly do anything digital?
Thanks in advance for your help.

---

### Post by ian dobson on 2008-10-19
Hi,

Digital TV (SD & HD) doesn't need alot of CPU to record programs as the signal is delivered to you already encoded. All the CPU has to do is split off the data that it wants and write it to the disk.

Recording 2 SD channels from a MPEG hardware encoder (PVR-500) uses about 4-6% CPU on one core on my Quad Core system.

Playback is something totally different. As long as your recordings are in MPEG-2 format and your Graphic card supports hardware decoding (vX) then the CPU has almost nothing to do. On my frontend (Core2Duo E5200 with a Nvidia 7300LT graphic card) needs about 8% CPU to play SD video (720x576). To play back HD the CPU load goes upto about 85%.

So to answer your question your hardware should be sufficient to record/playback SD television.

SD television is standard definition at 720x576 pixels
HD television is high definistion at upto 1920×1080pixels.

Have a look here for more info [http://en.wikipedia.org/wiki/High-definition_television](http://en.wikipedia.org/wiki/High-definition_television)

Regards
Ian Dobson

---

### Post by bglaze1 on 2008-10-19
Thanks Ian.  
So recording video streams shouldn't take much power, but to display them will take more power.  I am not looking to playback HD video right now.  I just want to know would I be able to handle displaying SD video at 720x576 without much problem, given my system (P4 1.8GHz processor, NVIDIA GeForce FX5200 AGP card with 256MB DDR, and 2GB RAM)?  

Does my graphics card support hardware decoding (vX)?  I assume it does, it is fairly common card on these forums.

Is there some setting you set in Myth that tells the system that you are only displaying in SD so that it won't load up your CPU while doing all the decoding for HD?  Or is there a way to capture the stream initially in SD so there is no conversion necessary?  

The reason I ask is all the video capture cards I have been looking at have minimum requirements of 2.2-2.4GHz processors, but since it doesn't take much processing power to capture the video, why would they have such a high requirement? 

Would I still be able to use them in my system and somehow just capture SD video?

---

### Post by SiHa on 2008-10-20
I have an identical setup, my frontend is a P4 2GHz, FX5200, 2GB Ram. I have Myth set to a CPU+ playback profile so that the decoding is done in software. Decoding SD and scaling to 1280x720 takes about 15% CPU. So yours should be fine. 

You set the playback profile to **CPU-** or **CPU--** to make use of the hardware decoding, it's in TV setup -> Playback, I think.

I use software decidong, because if an incompatibility problem  do with the bits you have to enable to get Chromakey enabled (to use a colour OSD). This caused a problem that kept on giving me buffer underruns on the audio, so I switched to CPU decoding and all is rosy. I believe this is being addressed in 0.22.

As far as capture is concerned you will capture at the resolution the programme is broadcast in, so SD broadcast will be captured as an SD MPEG stream. Decoding this with your machine should be no problem, even without the HW decoding.

---

