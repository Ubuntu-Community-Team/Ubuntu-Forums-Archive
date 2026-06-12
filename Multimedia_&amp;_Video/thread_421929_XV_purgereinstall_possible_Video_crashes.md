---
title: "XV purge/reinstall possible? Video crashes"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Ferrat on 2007-04-24
Well been looking around and seems more ppl than me have this problem.. 

Just upgraded from 6.10 to 7.04 without any problems

Got everything running almost instantly 3D acc ect. and everything was fine, 

But then my computer crashed during watching a Movie with VLC and playing WoW at the same time, I know the crash was from WoW (99,99%) and this has happened before on a numerous occations.
So I just rebooted like I allways do, started up WoW no problem, started the movie and BOOM
my xserver crashed and got restarted, hmm weird, so I tried restarting the movie without WoW, BOOM, same thing again.. 
WTF? well reinstalled VLC 
Tried again.. same deal.. 

Tried reinstalling VLC again and my ATi drivers and rebuilding the core but same thing.. 
I purged all gstreamer and ubuntu-desktop ect. and reinstalled.. 

No change.. 

Found after a bit of testing it was the XV that crashed all the time, players work aslong as they don't use XV but I want XV, I know it worked before without problems and I like VLC. 

Is there any easy way of purging and reinstalling XV to fix this? 
Since removing Xvidtune removes more or less every single thing used by Xserver including xserver it self when you want to remove it. 

Any way to restore it? or do I have to more or less do a full reinstall?](*,)

---

### Post by Ferrat on 2007-04-24
no one knows why this could have happened or how to fix it without more or less total reinstall?

---

### Post by arnold mous on 2007-08-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34776](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34776) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You can't do much other than make a bug report. 

I have the same problem.

in /etc/mplayer/mplayer.conf 

change 
vo=xv
to 
vo=gl

Or something like that to avoid XV. You can also try use the free NVIDIA drivers.

---

