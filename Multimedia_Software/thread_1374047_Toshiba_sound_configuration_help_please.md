---
title: "Toshiba sound configuration help please"
date: 2010-01-06
forum: Multimedia Software
---

### Post by brown12 on 2010-01-06
Status: system installed, sound working on the speakers.

Symptoms:

[LIST=1]
[*]No audio in, with PulseAudio device Analog Stereo Duplex chosen, either with integrated mic or 1/8" mic jack. It would be great if each would work independently.
[*]When headphone is plugged in, speakers continue to run. It would be great if they'd turn off.
[/LIST]

Hardware: Toshiba Satellite T135-1309 laptop
OS: Ubuntu 9.10 Karmic, fresh install yesterday afternoon.

Fixes tried: attempted to configure several options alsa-base.conf
>  snd_hda_intel model = toshiba >  snd_hda_intel model = auto >  snd_hda_intel model = satellite Output from alsa-info.sh information gathering script [here]("http://www.alsa-project.org/db/?f=c42bbf543a349a0e86d557ed4c6d85963e101d8a").

I believe my PulseAudio packages are up to date--I've read several guides at Ubuntu forums and PulseAudio wiki.

Many thanks!

---

### Post by brown12 on 2010-01-09
bump

---

