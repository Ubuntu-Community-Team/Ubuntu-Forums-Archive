---
title: "NVP prebuffering pause on HD playback"
date: 2008-04-18
forum: Mythbuntu
---

### Post by Slacker3k on 2008-04-18
I've seen a lot of issues posted about choppy HD playback with the NVP Prebuffering Pause error, but nothing seems to tackle my problem.

System:  Frontend/Backend single system
Processor:  AMD 64 - 3000
Memory:  1GB
Video Card:  FX5000 - Proprietary Drivers

Recordings made with my HD3000 playback fine via VLC (processor only runs abouyt 50%) but stutters in Mythfrontend.  I've tried every preset for playback and they all suffer the same symptoms - some worse than others.

I also created my own playback rule and have gone through all the possible combinations of settings and cannot find one that fully works.

All of them playback with fairly frequent stutters in audio/video and output the NVP error.  Any ideas?  Let me know what other information you might need!  

Thanks!

---

### Post by Slacker3k on 2008-04-24
Still frustrated by this issue, but I've done some more testing, so maybe some more information might help:

1)  I've played around with different playback profiles and have found that some work better than others.  The most frustrating thing is that some work better with SPECIFIC HD recordings.  Why would this be?

2)  I've tried to use an add-on sound card (Riveria) hoping to maybe offload some processing.   Doesn't seem to help, but I'm also wondering why my onboard soundcard which is disabled in the BIOS, still shows up.

Still trying...  I'll try anything.

---

### Post by colinnwn on 2008-05-21
Did you figure anything out?  I'm having the same NVP prebuffering pause problem.  I believe mine only manifests when the backend is recording while I play a recorded show.  It usually (but not always) happens while recording and watching different shows.  It seems to always happen if I start a recording, wait 10 minutes, then try to start watching that same show in delay.

---

### Post by volkswagner on 2008-05-21
Does live TV work better than playing a recording.  I have the same nvp issues.  It happens on all my frontends.  It does not matter if recordings are via my firewire connected cable box on master backend, nor my Kworld recordings via QAM on my slave backend.  The odd thing is usually (99%) live tv plays flawless.  I do get audio errors but no nvp pause.  Here are my threads.

[http://ubuntuforums.org/showthread.php?t=753433]("http://ubuntuforums.org/showthread.php?t=753433")

 [http://ubuntuforums.org/showthread.php?t=787317]("http://ubuntuforums.org/showthread.php?t=787317")

Sorry I can't help.  I would just like to know it our problems are related.

---

### Post by novellahub on 2008-05-21
What playback profile are you guys using?  If CPU+ is used, it kick in XvMC to help with HD playback. I have found CPU++ is the best setting on mine (AMD 3800X2) and my brother's machine (AMD 3200+).

Also, do you guys have nvidia video cards?  I have found without the following tweak, xorg cpu usage goes sky high during playback:

[http://knoppmyth.net/phpBB2/viewtopic.php?t=18119&highlight=useevents](http://knoppmyth.net/phpBB2/viewtopic.php?t=18119&highlight=useevents)

I have this change on my Knoppmyth R5.5 RC14 and my brothers Mythbuntu 8.04 setups.

---

### Post by Dewey_Oxberger on 2008-05-24
I had 7.10 Mythbuntu working great on this rig.  (abit AN-M2HD (NVidia based 7050PV), dual core athlon x2, 2 Gig, 250 G Seagate HD).

I got a new (larger) HD and have spent the last month of free time trying to get 8.04 to work at least as well as 7.10.  Lots of show stoppers, lots of minor problems.

Now I'm down to this problem.  NVP Prebuffer Pause in the logs for the front end.

I only have HD on this system (HDHomeRun tunner) and the problem always happens when the On Screen Display is being rendered.  I can see jittery pixels in the OSD and the audio stutters and the video seems to be skipping frames.

---

### Post by 7.11brown on 2008-07-31
doing the cpu ++ change worked for me.  My original problem was that just starting HD would cause prebuffering....CRASH.  Now just slight jitter while changing between HD's.

Stats.  Celeron D 2.8
512 mb ram
80 gb (ide) 500 gb (sata) Hd's
pvr 350 and HDHR
all in one front/backend
mythbuntu 8.04 32 bit

---

### Post by abbygirl on 2009-10-24
> **Dewey_Oxberger said:**
> I had 7.10 Mythbuntu working great on this rig.  (abit AN-M2HD (NVidia based 7050PV), dual core athlon x2, 2 Gig, 250 G Seagate HD).

I only have HD on this system (HDHomeRun tunner) and the problem always happens when the On Screen Display is being rendered.  I can see jittery pixels in the OSD and the audio stutters and the video seems to be skipping frames.

I have the exact same issue.  Has anyone solved this?  I find this thread in google quite a bit but no solution listed.  It's maddening!  Thanks!

---

### Post by Crash87ss on 2009-10-26
hey, 

If it is only recordings your having a problem with (and recordings work everywhere except myth) try turning "preview recordings" off. Its under one of the setup menues, probably General. This worked for me! 

Post back if and if it works/doesn't work. Might be a bug of sorts. 


[http://ubuntuforums.org/showthread.php?t=1277332](http://ubuntuforums.org/showthread.php?t=1277332)

---

