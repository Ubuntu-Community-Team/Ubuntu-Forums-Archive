---
title: "Numerous Issues (X cpu hog, backend segfaults, more)"
date: 2008-07-14
forum: Mythbuntu
---

### Post by netslacker on 2008-07-14
I am having numerous issues with my Myth box.  None of these are new, I've just never been able to resolve them all since building the box.  Any insight into any of these would be helpful.

1. Mythbackend crashes.  About once a day or once every two days mythbackend crashes for no reason.  I've searched every log file and the only thing I can find is a "segfault" error on one line.  This can happen when there is NO activity with the box or when there is activity (recording). I setup "monit" to monitor the mythbackend process but this is only a bandaid approach as it can crash while recording - not good.

2. Mythfilldatabase segfaults.  Again, not sure why, the only thing I can find in any log is reference to a segfault.

3. X kills my CPU.  This isn't a problem EXCEPT that when it is sucking up 100% cpu that the system is unresponsive to remote control commands.  Seems to be intermittent and varies for no reason because if you watch it on "top" X varies between ~7% to 100% while watching a show. While it's at 100% the system will not respond to any input. Very annoying.

I am running a newly built system:
gigabyte GA-MA78 ATX mobo
Biostar nvidia 7200GS
AMD 5000+ 64 X2
2gb ram
Seagate SATA drive

---

### Post by theophile on 2008-07-14
Segfaults can sometimes be caused by overheating. Is your box adequately cooled?

---

### Post by netslacker on 2008-07-14
> **theophile said:**
> Segfaults can sometimes be caused by overheating. Is your box adequately cooled?

Yes.  I have the Silverstone LC20M.  I am using the Arctic cooler on the CPU (which runs ~40 degrees C under load) and have two case fans to vent the case.  I have also run for a time with no case lid and experienced the same problems.

I'll also note that I am running MytbBuntu 8.04 64bit version.

Is there any stability gains in going to the 32bit version? does anyone know?  Since I only have 2gb of ram I don't really need 64bit so if there are stability gains I'd be happy to go there.

---

### Post by mrand on 2008-07-14
> **netslacker said:**
> Yes.  I have the Silverstone LC20M.  I am using the Arctic cooler on the CPU (which runs ~40 degrees C under load) and have two case fans to vent the case.  I have also run for a time with no case lid and experienced the same problems.

I'll also note that I am running MytbBuntu 8.04 64bit version.

Is there any stability gains in going to the 32bit version? does anyone know?  Since I only have 2gb of ram I don't really need 64bit so if there are stability gains I'd be happy to go there.

If you have nothing else to loose on your system, you might as well try it.

Before doing that though, I'd run a boot-time RAM test for as long as you possibly can.  Overnight and let it keep running through the next day until you get home from work?    Another alternative is to try running with one stick of memory at a time.

Sorry that I don't have any ideas for the 100% cpu.

Good luck,
[INDENT]   Marc[/INDENT]

---

### Post by ian dobson on 2008-07-15
Hi for the 100% CPU usage what settings are you using for your video playback?

There are the options CPU++,CPU+,CPU-,CPU-- and Standard. Try changing to using a slightly less taxing ++ to +.

My frontend 1.33GHz Core2 with a 7300GS does SD video to my analog TV and only seems to use between 7-15% CPU using the "standard settings".

Also have you installed the NVIDIA drivers rather than the open source/VESA ones?

Regards
Ian Dobson

---

### Post by netslacker on 2008-07-15
> **ian dobson said:**
> Hi for the 100% CPU usage what settings are you using for your video playback?

There are the options CPU++,CPU+,CPU-,CPU-- and Standard. Try changing to using a slightly less taxing ++ to +.

My frontend 1.33GHz Core2 with a 7300GS does SD video to my analog TV and only seems to use between 7-15% CPU using the "standard settings".

Also have you installed the NVIDIA drivers rather than the open source/VESA ones?

Regards
Ian Dobson

Hi, I am using CPU++ but I don't believe this to be the problem.  For the most part, when playing a video, CPU is ~40% however, during the play it will drift up to 100% and stay there for a minute or so, then drift back to ~40% (or less).  When it's pegged, there is no response from remote control until it drifts back.  I have applied the "renice -10 <pid>" command to the X process as documented in the wiki (mythtv.org) but this has only marginally helped.

I am running the 169 driver, which is what is in the repository.  I plan to try updated drivers when I get another break and can spend some time on it.

---

### Post by mrand on 2008-07-15
> **netslacker said:**
> Hi, I am using CPU++ but I don't believe this to be the problem.  For the most part, when playing a video, CPU is ~40% however, during the play it will drift up to 100% and stay there for a minute or so, then drift back to ~40% (or less).  When I previously said I didn't have any ideas, I was referring to some unknown problem with X.  If you're only seeing these cpu peaks when Mythtv is active, it sure seems like trying a different profile would be a quick and easy test before going to the trouble of changing drivers or anything.

According to the [Mythtv wiki]("http://www.mythtv.org/wiki/index.php/Playback_profiles#CPU.2B.2B_default_settings"):
> CPU++ is a profile group designed for systems capable of software rendering. It does not take advantage of XvMC for MPEG-2 decoding. 

When you say "X kills my CPU", does it do that when running VLC or mplayer, or only Mythtv.  If only under Mythtv, again, it sounds like profile.

[INDENT]Marc[/INDENT]

---

### Post by netslacker on 2008-07-16
> **mrand said:**
> When I previously said I didn't have any ideas, I was referring to some unknown problem with X.  If you're only seeing these cpu peaks when Mythtv is active, it sure seems like trying a different profile would be a quick and easy test before going to the trouble of changing drivers or anything.

According to the [Mythtv wiki]("http://www.mythtv.org/wiki/index.php/Playback_profiles#CPU.2B.2B_default_settings"):


When you say "X kills my CPU", does it do that when running VLC or mplayer, or only Mythtv.  If only under Mythtv, again, it sounds like profile.

[INDENT]Marc[/INDENT]

Thanks, Marc.  I have changed to the "Normal" profile and even the CPU- profile and X still drifts to 100% cpu.  The error I am referring to appears to fit very well with this description:

[http://www.mythtv.org/wiki/index.php/Optimizing_Performance#XORG_CPU_Hogging](http://www.mythtv.org/wiki/index.php/Optimizing_Performance#XORG_CPU_Hogging)

and since the offered solution only minorly helps I was hoping someone else may have a better solution or suggestion.

I will try it w/ either VLC or MPlayer but since the system does not have a keyboard/mouse and is solely connected to my tv that will take me a bit to do.

---

### Post by mrand on 2008-07-16
> **netslacker said:**
> Thanks, Marc.  I have changed to the "Normal" profile and even the CPU- profile and X still drifts to 100% cpu.  The error I am referring to appears to fit very well with this description:

[http://www.mythtv.org/wiki/index.php/Optimizing_Performance#XORG_CPU_Hogging](http://www.mythtv.org/wiki/index.php/Optimizing_Performance#XORG_CPU_Hogging)

and since the offered solution only minorly helps I was hoping someone else may have a better solution or suggestion.

I will try it w/ either VLC or MPlayer but since the system does not have a keyboard/mouse and is solely connected to my tv that will take me a bit to do.
Slim might be the best profile to try, but there is always the possibility that it isn't profile related.  Sorry to hear the link you found didn't help either.

As for keyboard/mouse - you could always enable VNC for a little while and control it from remote (although know that VNC might bog you down further).

[INDENT]   Marc[/INDENT]

---

