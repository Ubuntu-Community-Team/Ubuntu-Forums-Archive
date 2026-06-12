---
title: "Live Tv and Playback performance problems after .24 upgrade"
date: 2011-04-03
forum: Mythbuntu
---

### Post by lmclaren on 2011-04-03
Hi,

I had been running 10.04 LTS with .23 for over 12 months with no problems, I have recently upgraded Mythtv .23 to .24 without changing the OS. (changed the repo and apt-get distupgrade)

Since the upgrade to .24 I have been having problems on the combined frontend with pausing during playback of live tv and recorded.
Videos seem a lot better than the tv but may have some problems.

A remote front end that connects to the combined front end is having greater problems, it too is pausing but also suffers from picture breakup (blockies).

Neither had problems before the update.

The combined frontend is a core 2 with 2GB of ram, the video card is a geforce 210.

The client only is a Acer Revo.

I have checked the front end and backend logs and am not seeing anything that looks like it may be the problem.

The CPU utils looks very low, less that 10%.

Can anyone suggest what to check further?

thanks

Lee

---

### Post by uteck on 2011-04-04
[SIZE="2"]I had the same problem after I upgraded.  On each frontend, go into the Settings and menu, then the Playback options, and turn **off **the real-time priority threads.[/SIZE]

---

### Post by lmclaren on 2011-04-04
I am giving the "no real time" a test on the front.

---

### Post by lmclaren on 2011-04-04
Hmmm, it may be better. I will keep testing. I can be a bit hard to spot, sometimes it is ok and other times it will pause 3 times in 5 seconds.

Lee

---

### Post by uteck on 2011-04-05
You should also check to see if the playback options are using VDPAU for decoding.  Perhaps it got reset to a default mode that is not working well.

---

### Post by lmclaren on 2011-04-05
Looks like I still have problems, I experienced my first ever hard lock up last night while watching recorded TV on the combined front / backend. The video froze on the screen and the audio repeated a 1 secondish loop.

The machine would not respond to KB or ssh, had to hit the power switch.

There is not a mention of any problems in either the syslog, mythfrontend or mythbackend logs.

I am not running with any Myth debugs switched on.

I have made sure that real time is off and the video settings are correct as well as doing an audio devices scan after the upgrade.

Any hints on where to start? I feel it in my waters that it my be i/o based but it is only a feeling with no hard evidence.

best regards

Lee

---

### Post by dibuntux on 2011-04-06
Hi, I also have performance and other playback problems in may HTPC with frotn/backend after upgrading to 0.24 from 0.23; OS remains 10.04LTS AMD64, to remain linear with my main workstation, that also works as a second frontend.

When the system is or has performed recording, the WatchTV function now takes 10 second to lock unto channels, whereas it normally takes less than 2 seconds. You got the "partial lock" message and then the video appears, but the message is still there. Then you get the message "you should have a lock on channel...blabla - press OK". And sometimes frontend just locks up; you can exit and restart the frontend but sometimes just does not work and have to restart the PC.
That never happened with 0.23, but not even a month or so ago: I keep upgrading to the latest PPA whenever there's one.

I'm testing the  "no real time" option and seems to be better, still not on par with 0.23. All and all I regret the upgrade.

Any other ideas?

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
2 WD Sata2 CaviarGreen 
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by lmclaren on 2011-04-06
There is mention of this problem on the mythtv-users mailing list, A number of people have posted re the problem.


[http://www.gossamer-threads.com/lists/mythtv/users/475779](http://www.gossamer-threads.com/lists/mythtv/users/475779)


I wonder why more people aren't seeing it?




Lee

---

### Post by dibuntux on 2011-04-07
Interesting, different though. I have never had a "Alsa buffer underun error". I do get pauses of 2 seconds during playback, whereas on .23 I had none (the HW is adequate and on SD video).
So is just .24 fixes... guess we have to wait for developers to fix it up.
The no lock on channels is more serious: now everytime after a recording watchtv becomes a problem, not being able to lock on channels, or locking on it after 10 seconds.
I'll keep testing and trying to be more sistematic on getting problems.

Thanks

---

