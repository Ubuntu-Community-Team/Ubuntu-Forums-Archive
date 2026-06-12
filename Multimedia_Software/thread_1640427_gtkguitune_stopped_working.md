---
title: "gtkguitune stopped working"
date: 2010-12-07
forum: Multimedia Software
---

### Post by aske on 2010-12-07
Hello,

I have been using this fine tuner, however some days ago it wouldn't open any more.

In the console I get the following:

```
usage: gtkguitune [--option [<arg>]]
  options:
     [...]

initializing audio at /dev/dsp
/dev/dsp: No such file or directory

```

I don't know much about the sound issues of the system (alsa, oss etc).. everything else (players and audacity) is working fine (and hope to keep it that way :) ).

Any suggestions?

Thanx.

---

### Post by ikt on 2010-12-31
> initializing audio at /dev/dsp
/dev/dsp: No such file or directory

Same issue, I'm assuming this is because I don't have something plugged into the digital output of my sound card?

---

### Post by jsampaio57 on 2011-02-20
> **ikt said:**
> Same issue, I'm assuming this is because I don't have something plugged into the digital output of my sound card?

use

$ padsp gtkguitune
cheers...
Jorge

---

### Post by practic on 2011-05-02
That command got it to run, but the display was jerky and did not seem to respond properly to input. I'd recommend lingot or fmit, both of which work well (or TuxGuitar, which has a Guitar Tuner tool).

---

