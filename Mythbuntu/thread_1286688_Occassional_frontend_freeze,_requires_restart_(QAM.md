---
title: "Occassional frontend freeze, requires restart (QAM 256)"
date: 2009-10-09
forum: Mythbuntu
---

### Post by the_pod on 2009-10-09
Hi.  Had my Mythbox up and running for 2 or 3 months and generally love it.  Next step on my plan is to place it in another room so and run cables so that the computer noise is inconspicuous.  However, right now I'm not feeling comfortable moving everything because it seems to need a reboot at least once a week.

**My specs:**

* Mythbuntu 9.04, weekly updates
* ATI Radeon HD 3200 onboard video
* 3G ram
* 1TB HD
* Hauppauge 1600 & 1250 inputs
* Capturing QAM 256 exclusively (direct hookup)
* Connected to 47" LCD via HDMI
[B]
Issues:[/B]

*  Issues are typically with less than perfect digital signal channels
*  For a while MythTV would crap out and just shut down the front end and leave me looking at the desktop.  Updated the V4L drivers and this seems to no longer happen.
*  Now, on these same types of videos where the signal is less than perfect the frontend just locks up.  Frame freeze, actually.
* Can tab out and force a frontend shutdown but this obviously isn't ideal

**Observations:**
*  On these videos, the machine is unable to flag for commercials - process simply will not complete.
*  The freeze occur in the exact same place in the video.  Was watching a show last night and managed to recreate the freeze on the same scene of the same show on 4 occasions
* On the 1st freeze I left the machine running for about 10 minutes in hopes that it finished recording the show I was watching (I was watching a delay).  This proved successful as the recording was able to fully complete, however the frontend was no longer responsive (frozen). 


If anyone has had similar problems and can help me debug the system that would be fabulous.  Right now MythTV takes some patience from the wife due to the need for occasional resets and I would really like to make this a permanent (and less hands-on) component of the system.

I imagine I need to look through the log files but not being a Linux or log-file expert I have no idea what to look for.  Could someone help?

Thanks for reading.

---

### Post by the_pod on 2009-10-13
(pity bump for myself with new info)

Ok.  It happened again tonight and I got off my lazy butt and grabbed the logs.  Like I said, I don't much speak log file so I'm hoping for some generous souls that care to enlighten me.

I'm thinking there may be a frame sync error here: ```
==> /var/log/mythtv/mythfrontend.log <==

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.619 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.620 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error

2009-10-13 20:10:13.621 [ac3 @ 0xb7467744]frame sync error
```

Didn't find anything related on a forum or even Google search that made sense to me.

About the same time I see this stretch in a different log file stream:```

==> /var/log/mythtv/mythbackend.log <==

2009-10-13 20:09:28.734 ProgramInfo, Error: GetPlaybackURL: '3032_20090921190000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.737 ProgramInfo, Error: GetPlaybackURL: '3032_20090923190000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.738 ProgramInfo, Error: GetPlaybackURL: '3032_20090923210000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.742 ProgramInfo, Error: GetPlaybackURL: '3038_20090924233000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.748 ProgramInfo, Error: GetPlaybackURL: '3004_20090925193000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.750 ProgramInfo, Error: GetPlaybackURL: '3032_20090927100000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.751 ProgramInfo, Error: GetPlaybackURL: '3050_20090927110000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.753 ProgramInfo, Error: GetPlaybackURL: '3050_20090927120000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.754 ProgramInfo, Error: GetPlaybackURL: '3032_20090927120000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.755 ProgramInfo, Error: GetPlaybackURL: '3032_20090927160000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.756 ProgramInfo, Error: GetPlaybackURL: '3032_20090927170000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.757 ProgramInfo, Error: GetPlaybackURL: '3032_20090927180000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.759 ProgramInfo, Error: GetPlaybackURL: '3032_20090927190000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.761 ProgramInfo, Error: GetPlaybackURL: '3050_20090928020000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.763 ProgramInfo, Error: GetPlaybackURL: '3032_20090928190000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.771 ProgramInfo, Error: GetPlaybackURL: '3038_20090930033000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.773 ProgramInfo, Error: GetPlaybackURL: '3032_20090930190000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.781 ProgramInfo, Error: GetPlaybackURL: '3032_20090930200000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.782 ProgramInfo, Error: GetPlaybackURL: '3032_20090930210000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.792 ProgramInfo, Error: GetPlaybackURL: '2850_20091007003000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.802 ProgramInfo, Error: GetPlaybackURL: '2981_20091009200000.mpg' should be local, but it can not be found.

2009-10-13 20:09:28.810 ProgramInfo, Error: GetPlaybackURL: '2911_20091013093000.mpg' should be local, but it can not be found.
```

If anyone can help I'd really appreciate it. These may or may not be red-herrings, but it seems on target I'm thinking.  

From what I can tell, the error (last 2 times) has been specifically with NBC, digital, non-HD, QAM.

Thanks in advance.

---

### Post by Caysho on 2009-10-15
Searching on ```
frame sync error
``` in google finds [this mythtv ticket]("http://svn.mythtv.org/trac/ticket/6454").

I am guessing the GetPlaybackURL error means it cannot find the file.

---

### Post by the_pod on 2009-10-15
Many thanks.

Per the comments following that:

> 
    *   status  changed from new to infoneeded_new

Can you retry with current trunk? We've had a ffmpeg resync which might have helped.
Changed 3 months ago by databubble ¶

Under 20842 I am no longer seeing any sync errors, thanks. The resync seems to have solved the problem, and commflag is working fine.

Good work.


Having never done a trunk update, should I simply enable the trunk repos for one update (don't necessarily want to have it on all the time as it seems more prone to potential performance problems as per [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds), or so is my understanding) or is there an optional preferred method?

Also, would this push me to the .22 level as I'm not sure I want to do that just yet?

Thanks for your reply. I really appreciate it.

---

### Post by Caysho on 2009-10-15
If you enable the trunk repository for one update only, then remove it, your install will revert during the next update, assuming you do another.

I figure the trunk install is unsupported.  I do not know of a preferred method of achieving what you are after.

The trunk packages are at 0.22 - have a look at the [PPA list]("http://ppa.launchpad.net/") and search for myth, you will see both the older trunk and newer 0.22 set.

---

### Post by the_pod on 2009-10-28
As an update, this particular issue has really been bugging me.  

Monday was watching the Eagles / Redskins game and the front-end just kept crashing.

I was about to take the plunge and buy an NVidia card in the hopes that this would solve the issue (resulting in the question from the wife: "Ever feel like you're being $40 dollar-ed to death?" Answer - yes.) 

Before hitting "buy" at NewEgg, I decided to go off-road and try installing the latest version of the ATI Linux video drivers.  Had a couple issues with this as the required packages outlined in the ATI documentation are not found by name in Synaptic or using "apt get", however I rolled with it anyway.  

After installing, I was able to manually adjust my video to the 1920x1080 size.  I can't get this to remain as default after a restart, but I guess I can manually adjust whenever I restart which is not expected to be frequent.  Refresh rate is capped at 30 MHZ which seems low, but whatever.  

Rewatched the lousy MNF game through the parts where it kept crashing and successfully navigated through the video without a single front-end crash.  Success is mine.  Some artifacts remain in the video but it's not as bad.  At this point I'm working on the assumption that I have a weak cable connection to my house (Comcast has occasionally not been able to see the cable modem which adds a little credence to this theory) so I'm as good as I'm going to get within my current limitations.

Lesson for anyone out there with an integrated ATI 3200 experiencing FE crashes - upgrade your ATI Linux drivers outside of the repos.  

Regarding previous theories on the commercial flagging being a cause, I still may have issues there, but I'm ok with that as long as I don't have to keep restarting the FE.

Hope this helps someone down the road.

---

### Post by bcg30506 on 2009-12-03
I'm getting very frequent errors with this.  I just bought a Hauppauge 950Q QAM USB tuner yesterday and got it setup.  This gives me free HD local stations.  I can watch a show on it just fine, but any time I change channels I get the frame sync errors in the frontend log and have to manually kill the process as it accepts no input.  This also happens when I try to playback a recording from it in the LiveTV group which is odd because I was able to watch that same recording fine while being recorded via Watch Live TV.  I have an NVIDIA card with VDPAU setup and working great.  I do not run commercial flagging at all as it has never proven very useful for me.

I'm running the 2:0.21.0+fixes-22228-openglvdpau2-0ubuntu0 version from the repository plus avenard's.  I have no interest in moving to 0.22 until the problems are sorted out to try and keep the WAF high as until the addition of QAM, my box has been working great for a while.

---

