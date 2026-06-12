---
title: "mkv play ...not"
date: 2011-08-18
forum: Multimedia Software
---

### Post by bobk_nyc on 2011-08-18
so, I have these vid files, mplayer plays really unjsmoothe..vlc has no sound, and dragon player the sound is way out of sync...avis play good...btw, before when I had xp on this same machine, vlc played these same files with no trouble..so wat do I need?

---

### Post by papibe on 2011-08-18
Are those HD videos?
Maybe you need Video Hardware Acceleration to play them.
What is your graphic or integrated video card?

Regards.

---

### Post by drawkcab on 2011-08-18
Follow this guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Next, download SMplayer and enable vdpau if you have nvidia.  VLC should work too, but SMPlayer plays all my .mkvs w/out fail.

---

### Post by bobk_nyc on 2011-08-19
> **papibe said:**
> Are those HD videos?
Maybe you need Video Hardware Acceleration to play them.
What is your graphic or integrated video card?

Regards.

it is a Nvida agp card. can't see model

---

### Post by bobk_nyc on 2011-08-19
> **papibe said:**
> Are those HD videos?
Maybe you need Video Hardware Acceleration to play them.
What is your graphic or integrated video card?

Regards.

it is a winfast 340  Uled   128 meg  and I have  driver 173 activated, but it always says not curently in use

---

### Post by bobk_nyc on 2011-08-19
> **drawkcab said:**
> Follow this guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Next, download SMplayer and enable vdpau if you have nvidia.  VLC should work too, but SMPlayer plays all my .mkvs w/out fail.

well, I did all this, and the smplayer, is choppy, and has no sound  mplayer has sound and is synked as far as I can tell, but falls apatr after a minute.  vlc seems to not be choppy, but has no sound

what is vdpau?/ something I have ti install?

thanks

---

### Post by drawkcab on 2011-08-19
enabling vdpau offloads video decoding to nvidia gpu.  i'm not sure how to do that with wintec.   ???

---

### Post by papibe on 2011-08-19
According to [this]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Leadtek%20WinFast%20A340%20T%20128MB%20Graphics%20Card&v=Leadtek&uid=A340-T128&l=en-US&pf=1&pi=8&c=Graphics%20Cards%20%26%20Components&sc=Graphics%20Cards&os=32-bit&vd=all"), your Winfast card uses the [Geforce FX 5200]("http://www.nvidia.com/page/pg_20040109440047.html") chip.

Although that card is supported by the Nvidia driver. I'm (almost) sure that it does NOT have video acceleration (read [this]("http://www.mythtv.org/wiki/VDPAU")).

Anyway, to make sure your are using the proprietary Nvidia driver, and have VDPAU enabled,  follow the instruction on this [thread]("http://ubuntuforums.org/showthread.php?t=1823833").

Hope it helps.
Regards.

---

