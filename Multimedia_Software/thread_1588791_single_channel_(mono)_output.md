---
title: "single channel (mono) output"
date: 2010-10-05
forum: Multimedia Software
---

### Post by mrphd on 2010-10-05
Hi, does anyone know how I can force single channel sound output? I'm deaf in one ear and want to mix the channels (especially when I need to use headphones).
Thanks.

---

### Post by RaumTrug on 2010-10-06
if you wanted to use pure alsa, uninstalling pulseaudio, it'd be pretty easy: you could use an .asoundrc or an asound.conf, using the "route"-plugin to mix stereo to mono. of course you should watch to have a "dmix" somewhere in the line, to have multiple apps output at the same time. but then you'd miss pulseaudio, all other stuff it brings (like leveling apps with pavucontrol, using multiple sounddevices simultaneously, or the volume-controlling thing in the panel - you'd have to use an alsamixer instead, or find some ppa that's gosting around with an alsa-compatible volume control).

I don't really know about pulseaudio other than that I'm trying to get rid of it as soon as I install some ubuntu...it's possible to get an equalizer-module for it, so it would surely be possible to find/make some sort of "mixer" the same way. maybe even with simple config-file editing, like it's possible with pure alsa.

maybe it's even possible to create an alsa config, and force pulseaudio to go through the alsa-"route"-plugin, configured to downmix stereo (& surround) to mono as it fits your needs. that'd probably be the easiest sollution while keeping pulse, but I'm not the übernerd to tell wether it's possible or not.

maybe someone else knows better? ...then this at least pushes your thread... ;)

---

### Post by lidex on 2010-10-07
> **mrphd said:**
> Hi, does anyone know how I can force single channel sound output? I'm deaf in one ear and want to mix the channels (especially when I need to use headphones).
Thanks.

Everything seems to be stereo these days. What side are you wanting to output? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mrphd on 2010-10-09
Thanks for your help. On my laptop I have:

[http://www.alsa-project.org/db/?f=7cceeed7ead36333a4719f0dabc45942c014ed4d](http://www.alsa-project.org/db/?f=7cceeed7ead36333a4719f0dabc45942c014ed4d)

---

