---
title: "How should on approach this playback issue (picture goes crazy red/green stripes)?"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by stiev3 on 2007-12-18
I have 3 systems up and running(2 using linuxmce/kubuntu 7.04, 1 running on ubuntu 7.10).  All have Nvidia chipsets (7050PV, 6100, 7300GT).  All have the latest drivers (100.14.19).  

All three have this issue:
Video play back fails at some point.  I get sound, nothing locks up, but the picture goes haywire.  We'll go with the 7.10 system as my example.  I can run mythtv once on the system.  Should I close it and then start it back up, the picture is forever borked.  I need to restart X to get it back, but again should I close mythtv at any point after that, I can't play any video file properly until I restart X.

I'm using MythTV as my example here because I've been able to consistently repeat the problem; however, it has occurred on mplayer, totem, and VLC as well.  It's not as consistent with them though.

The other two systems have varying degrees of this issue, as in the picture displays the same kind of mess at random times, requiring an X restart.

I attached a screenshot, which is also here: [http://www.easyscreens.info/?v=1814](http://www.easyscreens.info/?v=1814) .

Where should I start in my troubleshooting adventure?

---

### Post by 6205 on 2007-12-19
i had the same artifacts on some avi and mkv files.

try install x264 package from repos and report back.

---

### Post by stiev3 on 2007-12-19
I've installed libx264 from the repos and still managed to run into the same issue (attached screenshot).

I don't think I noticed a difference, but I appreciate the suggestion.

---

### Post by 6205 on 2007-12-19
> **stiev3 said:**
> I've installed libx264 from the repos and still managed to run into the same issue (attached screenshot).

I don't think I noticed a difference, but I appreciate the suggestion.

:-(

---

### Post by coolen on 2007-12-19
I'm running into the same problem. Nvidia card here, with drivers from the repos.

I'm using the xine backend to totem, I've tried the gstreamer backend, and VLC can't handle it. It doesn't matter if Compiz is running or not.

I tried installaing x264. Should I log out after that? There was no change.


Scratch that. I really should have tried logging out before reporting back, but I was midway through writing my message.

Installing x264 worked. To the OP, that's the package x264, not libx264.

---

### Post by 6205 on 2007-12-19
> **coolen said:**
> I'm running into the same problem. Nvidia card here, with drivers from the repos.

I'm using the xine backend to totem, I've tried the gstreamer backend, and VLC can't handle it. It doesn't matter if Compiz is running or not.

I tried installaing x264. Should I log out after that? There was no change.


Scratch that. I really should have tried logging out before reporting back, but I was midway through writing my message.

Installing x264 worked. To the OP, that's the package x264, not libx264.


:-) yeah...i was gone crazy when half of my anime videos (like GiTS..) did not work in 7.10...

It looks like in 7.04 is x264 installed with depencies to mplayer, but not so in 7.10. There you must install it manually...

---

### Post by dannystaple on 2007-12-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hmm - x264 was already installed on my system - an upgrade from 7.04. I have not found the solution, but have found this defect report on launchpad.

I really want to sort this out, as having to reboot to watch tv regularly is becoming a pain... ](*,)

---

### Post by coolen on 2007-12-27
Do you have Wine installed on your machine? That was pinpointed as a possible cause in that thread.
If so, try using one of the working drivers (Xshm or OpenGL). Not sure how, since I'm on Windows right now, but it's worth a shot.

---

