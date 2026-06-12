---
title: "Display PCM volume?"
date: 2011-05-30
forum: Multimedia Software
---

### Post by az_s_za on 2011-05-30
I use PCM as my main volume controller, and have assigned some keyboard shortcuts for it.

I would prefer the volume notification applet and pop-up to show PCM volume instead of Master.  At present the pop-up only comes when changing the master channel and the panel icon shows master volume.

How can I change these to PCM instead?

---

### Post by az_s_za on 2011-05-31
[This script]("http://askubuntu.com/questions/12766/adjust-volume-via-commandline-so-that-volume-notify-pops-up/12769#12769") on ask Ubuntu solves my problem, in case there is anyone else with the same issue.

In that script I changed the mixer channel from 'Master' to 'PCM', then had my keyboard shortcuts run [FONT="Courier New"]*<script_name> up*[/FONT] or [FONT="Courier New"]*<script_name> down*[/FONT]

---

