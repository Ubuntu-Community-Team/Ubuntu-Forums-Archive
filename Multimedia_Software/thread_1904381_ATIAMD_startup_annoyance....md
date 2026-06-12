---
title: "ATI/AMD startup annoyance..."
date: 2012-01-04
forum: Multimedia Software
---

### Post by Xgen on 2012-01-04
Tried another forum (Precise) for an answer, but perhaps this one is more specific.

I bought a laptop with a ATI/AMD 6970 card. When rebooted into OO or PP the gamma is extremely light. If I start the Catalyst control center and then cancel it, it reverts to my custom settings. The settings are shown as saved properly, but not recognized on reboot. One suggestion was to go into the monitor 'Displays' and click 'Apply', but that didn't work.

With all my previous NVidia cards, I added 'nvidia-settings -load' to the Startup Manager to load my settings hidden...is there a equivalent ATI/AMD command or solution?

OR a hack....how to create a script to start and cancel amdcccle immediately at reboot - preferably a hidden window for esthetic reasons.

An annoying problem, but not the end of the world. It's just a challenge - doesn't look professional in an otherwise excellent distribution :)

---

### Post by Xgen on 2012-01-04
Found a solution through trial and error. Created a command in Startup Applications with a custom title and the command 'xgamma -gamma .660'. Works just fine at startup.

---

