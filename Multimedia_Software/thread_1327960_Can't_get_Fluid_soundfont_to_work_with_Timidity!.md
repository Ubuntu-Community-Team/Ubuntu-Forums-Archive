---
title: "Can't get Fluid soundfont to work with Timidity!"
date: 2009-11-16
forum: Multimedia Software
---

### Post by Kareeser on 2009-11-16
For all intents and purposes, I'm testing this using Sibelius 4 installed through wine.

I first installed the soundfont through apt:
```
sudo apt-get install fluid-soundfont-gm
```

Then I altered the timidity.cfg configuration file and uncommentd the appropriate lines.
```
source /etc/timidity/fluidr3_gm.cfg
source /etc/timidity/fluidr3_gs.cfg
```

When I tested it, the MIDI sounds got *worse* instead of better! They sound like the freepats sounds run through a tin can. Ugh.

I also tried linking directly to the soundfont - no results:
```
soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2
```

Did I do something wrong during setup?

---

### Post by Kareeser on 2009-11-16
Bumping for morning crowd

---

