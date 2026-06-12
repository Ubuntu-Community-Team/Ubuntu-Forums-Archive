---
title: "Choppy/Speedy Video"
date: 2009-07-14
forum: Mythbuntu
---

### Post by mcnever on 2009-07-14
Ok, i've been playing with mythbuntu for a couple of weeks now and its kicking my butt.
 
I'm not a linux guy, I'm hardly a 'computer' guy anymore, if it doesn't have cisco stamped on it somewhere i haven't touched it in years.
 
Anyway, i have a split frontend backend system (I plan on having 3 frontends when its all said and done).
 
I'm running mythbuntu 9.04 and I've been fighting an issues of choppy video since i got them up and running. my first thought was RAM, i only had 512, so i went out and got another 1G stick, didn't help. From what i've seen the most common response to this problem is 'check the DMA on your drive/dome kind of drive problem'. Had some issues telling if linux was using the DMA on the drive ( it was enabled in the BIOS). so i got fed up and went and got a SATA drive and moved my recording to that. I'm still running the system on the 250G IDE drive. After 3 hours of installing the drive (had to update bios and figure out that my mobo didn't support SATA2) I still have horrible video quality/no noticeable change. 
 
I did end up last night enabling frontend services on my backend and the video still looks the same there. so that kind of counts out the frontend as an issue right?
 
I'm not even sure what to look at this point, so... direct me... teach me... enlighten me.
 
My backend specs.
 
Athalon XP 2000
MSI KM4M-V
1.5Gig of Ram
hauppauge HVR1600
250 Gig IDE Drive
500 Gig SATA Drive
 
I want to make this work, but my lack of knoweldge of linux and all things multimedia is holding me back i think.
 
any help would be greatly appreciated.
 
Thanks
Jason

---

### Post by ahood on 2009-07-15
Hi Jason,

This sounds like a challenge to overcome.

There are a couple of questions that I would consider before identifying the culprit.

Are the video files choppy when viewing them with multiple video clients (xine, vlc, mplayer, etc.)?

If so, then this would rule out the off-chance that the choppy playback is specific to a particular video client. 

*Note: I have experienced choppy audio/video of a DVD import 75% of way through the recording using mplayer, but not with xine.*

Do these video files play choppy on another machine?

If the video files play fine on another machine, then this would indicate that the choppy playback is hardware related. 

Does the choppy playback occur when playing the videos on the backend machine that stores the files?

If so, then this would rule out the off-chance that the choppy playback is network throughput related.

What graphics card/chip (ATI, Nvidia, Intel, etc.), and driver version, are used to playback the video files?

What is the video source (hi-def TV, analog TV, DVD import, etc.), resolution (e.g., 720x480) and size (e.g., 1Gb) of the video files ?

Are other processes running in the background taking up system resources?

What is reported in the mythfrontend log file when playing the video file with the mythtv frontend?

*Note: Checking the log file is highly important and may give a clue that leads to the solution*

My best guestimate that might explain the choppy video is that the videos are hi-def recordings (3-5Gb, >720x480) played with hardware with insufficient CPU/GPU power to play the files. 

However, there are other causes of choppy video, such as other processes that limit system resources.

Hope this helps.

---

### Post by newlinux on 2009-07-15
If the files play okay in other players outside of myth (mplayer/vlc/etc.) first place I would look is to change your playback profiles. Some settings work better than others for different hardware. You may even need to make a custom one.

[http://www.mythtv.org/wiki/Playback_profiles#Default_profiles](http://www.mythtv.org/wiki/Playback_profiles#Default_profiles)

Also, I'd look in your frontend logs for clues as to what's going on.
What are your frontend specs (specifically, video card, CPU, monitor and how it is connected to that monitor). As asked above, what driver are you using for video card.

What kind of content are your trying to playback (HD, SD, etc.)?

---

