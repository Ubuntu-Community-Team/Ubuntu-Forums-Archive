---
title: "[SOLVED] Frustrating and weird problem!"
date: 2008-05-30
forum: Multimedia Software
---

### Post by medic2000 on 2008-05-30
I have an nvidia geforce go 7300 card on acer 4230 travelmate.I use nvidia-glx-new driver and Hardy Heron.My computer starts with compiz but when i move a window i see it's not smooth and it is slow. In nvidia settings there's only Auto and 60 Hz. If i change it when the compiz still working nothing happens. But if i first close the compiz then change it(whether to 60 or Auto not important)then started the compiz my desktop and windows became very very smooth.

What kind of problem is this? It haunts for long time and i decided to make a search for it.

---

### Post by wolfen69 on 2008-05-30
ive never had to use nvidia settings, but i heard you need to do
```
gksudo nvidia-settings
``` then make changes.

---

### Post by Sam Lars on 2008-05-30
If you go to System > Preferences > Advanced Desktop Effects Settings (if it's not there, install compizconfig-settings-manager), display settings, is "Sync To VBlank" (third checkbox) checked or not?  Try specifically unchecking it, but also checking it to see if that will help.

---

### Post by medic2000 on 2008-05-31
Solved:
It seems ccsm can't handle the refresh rate itself. In Ccsm-general-display settings unchecking the "Detect Refresh Rate" and tuning it manually works.

---

