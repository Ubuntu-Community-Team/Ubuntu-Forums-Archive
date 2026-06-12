---
title: "Anyone knows of an Antares Autotune or Melodyne like software?"
date: 2008-03-19
forum: Multimedia Production
---

### Post by angelsguitar on 2008-03-19
Hi.

I'm looking for a program or plugin to do pitch correction, something similar to Antares Autotune plugin or Melodyne software.  Does anybody knows about a similar program in Linux or LADSPA plugin format? Thanks.

---

### Post by Stochastic on 2008-03-19
I'm not aware of any auto-pitch-correction software in linux.  As far as I know, it's still at least a two step process:
1) run an FFT analysis to get the exact pitch values of the original sample (this can be done fairly easily in PD)
2) run a pitch adjust plugin to correct each note as needed (as much as I hate the rest of audacity, its pitch correct is quite easy to use)

but really, I must urge you to not use such horrid studio techniques; they're dishonest and help acts like pussycat dolls to be the 'musical stars' they are.

---

### Post by angelsguitar on 2008-03-20
> **Stochastic said:**
> I'm not aware of any auto-pitch-correction software in linux.  As far as I know, it's still at least a two step process:
1) run an FFT analysis to get the exact pitch values of the original sample (this can be done fairly easily in PD)
2) run a pitch adjust plugin to correct each note as needed (as much as I hate the rest of audacity, its pitch correct is quite easy to use)

but really, I must urge you to not use such horrid studio techniques; they're dishonest and help acts like pussycat dolls to be the 'musical stars' they are.

Please forgive my ignorance...What's PD? :confused:

---

### Post by Stochastic on 2008-03-21
PD or Pure Data is a graphical programming language where objects are connected in with each other via patch cords.  Logic structures and data flow chains are built by the user to their liking.
It takes a bit of learning, but not very much in relation to other musical programming languages (it is after all graphical) and it's quite powerful.

---

