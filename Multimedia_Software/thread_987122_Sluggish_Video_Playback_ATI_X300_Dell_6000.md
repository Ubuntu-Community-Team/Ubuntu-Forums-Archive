---
title: "Sluggish Video Playback ATI X300 Dell 6000"
date: 2008-11-19
forum: Multimedia Software
---

### Post by yahooking on 2008-11-19
Hello everyone i have  a Clean Install of 8.10 with COmpiz Removed Completly.
I am using a Dell 6000 Laptop with ATI X300 graphics. 
My drivers are FGLRX confirmed running. 
My question is when i am watching a Movie (Using Mplayer or VLC etc..) My Graphical Session Reboots itself...And i am then directed to the Login Window. My CPU usage is at 100 % when playing a video and i can tell that the computer and even sometimes the video is very sluggish. However when not playing any Video my system runs just fine. At one point my system shutdown thinking it was overheated... I have a Laptop Coolor running on full speed and my Fan in the system is Dust free and performing well (My Windows Xp sessions have never had problems running for months without reboots) I have 2 GB of ram and i have 2 GB of Swap dedicated. My CPU is an intel Centrino 1.8 ghz.
Why do i have compiz Disabled ?
* My Video is ALWAYS Sluggish when i have compiz Turned on.
* System is non responsive at times when i watch Youtube Videos.

My Xorg.conf file is at. [http://rafb.net/p/KSBtGW66.html](http://rafb.net/p/KSBtGW66.html)

Any Ideas ?
Thanks :D

---

### Post by CHaoSlayeR on 2008-12-04
Well...

...at first "Centrino" is not a CPU type at all, its only the name for a platform used by Intel for notebooks. Either you have a Pentium M, Celeron, Core, Core2, ...

...but now to your issue: for posting your xorg.conf please use the upload functionality and/or post it inline into CODE tags please.

First to the heat-problem: please confirm that your CPU scaling is working correctly.

Second to your video problem: please verify that AIGLX and DRI is enabled and working. If the system becomes unresponsive it may be because the video is processed completely by the CPU instead of the GPU which leads me to the problem that DRI and/or xv might not be enabled. So do a xvinfo to check if you have hardware accelerated video playback.

To your question > Why do i have compiz Disabled ? ...well, when it is > ...with COmpiz Removed Completly. it can't be enabled though. Curious why you even can turn on compiz at all: > ...when i have compiz Turned on

...so what is the case? Is it removed or not?

Regarding compiz with fglrx please also try following the instructions provided here: [Setup FGLRX with compiz-fusion]("http://forum.compiz-fusion.org/showthread.php?t=6794")

Greetz,

C]-[aoZ

---

