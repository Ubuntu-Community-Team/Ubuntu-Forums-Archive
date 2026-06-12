---
title: "Faint sound"
date: 2008-09-19
forum: Multimedia Software
---

### Post by mpcsm on 2008-09-19
Hi 
I'm new to this forum and 1st time user of Ubuntu, so please excuse may lack of knowledge.

I've a new laptop and managed to install Ubuntu 8.4 dual booting with Vista.

I've got all my devices working (including the wireless) but can't solve my sound card problem.

When playing system sounds or music the sound is there but very very faint.

Can I ask for someone to take a newbie through this issue!

I'm sorry I haven't provided any details (sound card make model, driver etc) because i don't know where to look and not very familiar with terminal commands.

All help would be appreciated.

---

### Post by markbuntu on 2008-09-19
You can go to my thread here for troublehsooting sound problems:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by cariboo on 2008-09-19
Have you tried double clicking on the speaker icon in the top panel and made sure the master and pcm are turned up?

Jim

---

### Post by mpcsm on 2008-09-19
Markbuntu: Thanks for the link. I tried to follow most of suggestions. I'm now using PulseAudio for all playback and can see the PuleAudio volume meter moving when the music is playing.

Issue remains same. The volume is too low and can hardly be heard.

Carriboo: yes all PCM and master volume at Max setting and not muted.

There has got to be a reason or even a conflict that is causing the sound being so low.

I also know its not hardware because I can hear the sound loud and clear under Vista.

Any other ideas?

---

### Post by markbuntu on 2008-09-19
In a terminal type aplay -l. Post the results here.

---

### Post by mpcsm on 2008-09-19
Mark Results below

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 4: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by markbuntu on 2008-09-20
You may be able to get help for you volume problem here. There are some specific configurations for your ALC883 that you can try:


[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by mpcsm on 2008-09-21
Mark Thanks. I'll read these links.

Are you able to answer this questions though....
Which of these is my sound card ALC883 or ALC268?

---

### Post by frankleeee on 2008-09-21
Have you just tried right clicking on the volume icon and opening the volume control and turning things up, and making sure your preferences pick for the icon control is one that is working best.

---

### Post by mpcsm on 2008-09-21
I'm running ALC268 (OSS Mixer).
Not sure if the following setting is correct but all of the Volume, Line-in, Mic, PCM-2, in0gain and Digital-1 are up and not muted.

Not sure if my sound card 268 or 883?

---

### Post by markbuntu on 2008-09-22
Your main sound card device is most likely the 883. The 286 may be used as part of the surround output or it could be part of the video HDMI output if you have that. Anyway, try switching your settings to the 883, see if that works.

---

### Post by mpcsm on 2008-09-22
Mark
Thanks. It made no difference.

I've tried to follow the instructions from the links you provided, but being a newbie, I ended up damaging the system so much that I had to reinstall and re-apply all the upgrades. 

I'm no good at recompiling kernels or downloading new ALSA drivers...Sorry :(
On the upside though, my ISP is getting rich :)

I've followed the instructions in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and CODE 
lspci -v
Results in

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Wistron Corp. Unknown device 4083
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fa204800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

I went to [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)
could not find ICH8 driver. 
Judging by the post...I'm out of luck....Would that be correct?

Is there a step by step trouble shooting that someone can help me with?

---

### Post by cariboo on 2008-09-22
Here's a shot of my sound preferences window. I have the same sound card.

Jim

---

### Post by Yellow Pasque on 2008-09-22
Your ALSA driver is called (snd-)hda-intel
Here's a link to a nice script to install the latest ALSA [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

You can also try OSS4 if that doesn't work (link in my sig)

---

### Post by mpcsm on 2008-09-23
Cariboo, I've change my settings to match yours and no success.

Temüjin, I used the script you provided, ran that as Sudo, 

1st upgraded to 1.07 completed ok but still no sound.
I ran alsamixer from the shell and get the following

ALSA lib simple_none.c:1741:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more
alsamixer: function snd_mixer_load failed: Invalid argument

Does that point to a problem??

2nd upgraded to 1.08 completed ok. I think that made it worse. I now have no mixer and the Volume icon on the tray is showing a red X.

alsamixer: function snd_ctl_open failed for default: No such file or directory

Looks like I'm facing another reinstall....Help

---

### Post by mpcsm on 2008-09-24
All
Any help would be appreciated ..Thanks

---

