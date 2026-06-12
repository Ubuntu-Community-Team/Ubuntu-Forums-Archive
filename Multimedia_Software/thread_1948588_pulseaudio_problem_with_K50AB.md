---
title: "pulseaudio problem with K50AB"
date: 2012-03-28
forum: Multimedia Software
---

### Post by hgreg20 on 2012-03-28
Hi all,

I have a strange problem with pulseaudio. Usually i just purge it right away, but i thought i might ask around a bit this time :)
About the problem: 
I have an Asus K50AB laptop, with VIA VT1708S sound codec ( lspci -> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) ). When i plug in my headphones sound gets muted (both internal speaker and headphone) and there's no sound until i unmute everything (there a lot of sliders: Master Front, Front, PCM, Center, LFE, Headphones, but it's really just two connector physically and internal mic + speaker)  in alsamixer or padevchooser, but if i do this, there's sound coming from both the internal speakers and headphones, and when i mute something then everything gets muted.

Is there anyone else with the same problem? Any solution maybe?

EDIT: by the way, everything is working fine when i purge pulseaudio

---

