---
title: "nVidia GEForce MX4000 and short xorg.conf"
date: 2010-07-28
forum: Mythbuntu
---

### Post by Barry_IA on 2010-07-28
Hi Folks!

Having problems with a FrontEnd (remote) computer; Mythbuntu 10.04, nVidia GeForce4 MX4000 (128 MB) in an IBM 8187 (3.0 GHz).  The problem is the display is jerky.  Discovered the nVidia driver wasn't installed so installed this morning; rebooted; didn't seem to help.

The xorg.conf file is very short -- only 18 or 19 lines.  This doesn't seem right as usually they go on several screens -- I was looking to change the TVOut line to SVIDEO and no such line.

Any suggestions on how to fix or would it be best to do a reinstallation (and what step did I overlook?)

TIA!

---

### Post by LowSky on 2010-07-28
What driver are you using? As far as I known the legacy driver might work for it, but that's it. What is jerky, Video playback? Is it trying to display HD content? I can tell you know the Geforce 4 series won't be able to do that. Just remember its an 8 year old card. It was designed before hi definition was even a thought for most consumers.

Xorg.conf hasn't been very "long" as you put it for a few years now. The info it contains has become very rudimentary and not so much needed as it used to be.

---

### Post by Barry_IA on 2010-07-29
> **LowSky said:**
> What driver are you using?

Hi LowSky!

(Quick reply as off to work shortly).  IIRC the system downloaded and installed the default driver for '96'.


> **LowSky said:**
> As far as I known the legacy driver might work for it, but that's it. What is jerky, Video playback? Is it trying to display HD content? I can tell you know the Geforce 4 series won't be able to do that. Just remember its an 8 year old card. It was designed before hi definition was even a thought for most consumers.

Yes, the video is jerky, and yes, trying to display HD, recorded at both 720 and 1080.  ...So the card is at fault, or probably more accurately not the right card for the job.  Might solve another problem: I was looking around to remember how to switch the card's output from VGA to S-Video (hence the looking in on xorg.conf).  Somewhere found the S-Video outputs 480i or 576i - downgrade of the display but better than nothing!  (The VGA output is sharp on an old CRT monitor, but movement is jerky.)

Looks like will be looking for a brand-new video card!  ...I'm going to mark this thread as 'Solved'.  Thanks again!



Xorg.conf hasn't been very "long" as you put it for a few years now. The info it contains has become very rudimentary and not so much needed as it used to be.[/QUOTE]

---

