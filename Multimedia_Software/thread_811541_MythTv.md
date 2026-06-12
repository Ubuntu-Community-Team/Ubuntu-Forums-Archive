---
title: "MythTv"
date: 2008-05-29
forum: Multimedia Software
---

### Post by SirOcelot on 2008-05-29
Ok. I am at wits end. Why? Well my dad's computer is equipped with a PVR-150 tv tuner. I have originally installed Ubuntu 8.04 then MythTv. That didn't work so I formatted and installed Mythbuntu. Same effect. For the last 3 days I have been searching for an updated (at least to Gutsy) HOWTO for setting up my TV Tuner, then MythTV for 8.04. Anything you guys need in terms of specs, just ask.

Oh and if anyone can double check for me on what Tv Tuner is in my dad's computer (which is a SONY Vaio VGC-RB57GY) and tell me if it is compatible with Ubuntu, it would be much appreciated. Thank you guys for all your help!

---

### Post by K.Mandla on 2008-05-29
Moved to Multimedia and Video.

---

### Post by issih on 2008-05-29
Its not very clear what is wrong from your post, you say myth tv and mythbuntu dont work...ok what actually happened? what packages did you install, what did you try to run, how did it fail?

This is the ubuntu documentation:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

There are definitely gutsy guides in there (no hardy yet though).

Your best bet is almost certainly to install mythbuntu control centre and then use that to install whatever else you require and work through the installation procedures. Myth tv is not a simple system to get up and running, it is a client server architecture with a backend database, and that means it can be a pig to configure, the trade off is you can watch tv on any networked pc in the house :) (Any linux pc definitely, mac intel yep, windows I'm not sure, although I think there is a viewer)

---

### Post by SirOcelot on 2008-05-29
Ah I apologize I wasn't clear. Well I installed the backend and upon setting up the capture card it says Probed Info: Hauppauge WinTV-PVR-150. The problem I am having specifically is I am getting no channels through my TV Tuner. I have ran mplayer /dev/video0 and nothing comes up on the screen. The cursor drops and waits for me to CTRL + C, but no picture.

I have even went as far as to install TV Time, but when I run it it flashes on screen and closes. So technically this is a Tuner problem, not a MythTV problem. Although when I do go into MythTV and scan for channels on us-cable I get no signal, even though it detects my TV Tuner.

*EDIT*
Apparently I don't have a PVR-150? On the Marketing Specs I pulled off of Sony's website for this model of computer I have a Giga Pocket MPEG2 Realtime Encoder board with TV tuner. Is this supported in Ubuntu?

*EDIT2*
Well I found my own answer [http://ubuntuforums.org/showthread.php?t=232668&page=2](http://ubuntuforums.org/showthread.php?t=232668&page=2)

---

