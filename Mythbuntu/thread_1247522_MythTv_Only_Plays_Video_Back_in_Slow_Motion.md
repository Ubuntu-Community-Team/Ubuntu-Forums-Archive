---
title: "MythTv Only Plays Video Back in Slow Motion"
date: 2009-08-23
forum: Mythbuntu
---

### Post by nbetham on 2009-08-23
Hi, I have a problem with MythTv setup where it will only play back video (including audio) in slow motion . I tried running the mythfrontend in verbose mode and it continuously says that the video is about 3 frames ahead of the audio and tries to speed it up but it never accomplishes syncing them. I'm pretty sure that it is a broblem with MythTv because TvTime displays the video no problem. 

My current setup is:
Intel DG45FC motherboard
Intel Core 2 Quad 2.33 ghz CPU
Hauppauge 1800 HVR   

Any help on this issue would be greatly appreciated.

Sincerely: Neil

---

### Post by xinix on 2009-08-23
I was having trouble with a channel that was playing in slowmotion including audio.  Enabling "Extra audio buffering" in Setup> TV Settings> Playback fixed this for me.  This may or may not work for you but its worth a try.  Have you tried different playback profiles?

---

### Post by nbetham on 2009-08-23
So, I tried enabling the buffer extra audio setting and it doesn't seem to have affected playback at all. The same goes for the playback profiles. I have attached the log file for MythTv if any one  would care to take a look at it, if you need any other information from my setup I would be happy to get it.

Thanks for the reply!

Sincerely: Neil

---

### Post by nbetham on 2009-08-24
Well after playing around a bit more it seems that MythTv is not the only app that has the slow mo audio and video problem. I tried using mplayer and it also has the problem, as well it failed to play more than a few seconds of video. Anyone have any ideas on what the problem is and how to fix it.

---

