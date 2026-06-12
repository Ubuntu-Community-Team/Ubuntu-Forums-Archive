---
title: "RANDR extension is not present?"
date: 2010-09-02
forum: Multimedia Software
---

### Post by Spektyr on 2010-09-02
I've been trying to get the dual monitors to work the way I want them to, so far no luck.  I read that xinerama would enable dragging between two X screens so I went to System -> Preferences -> Monitors and clicked the box for xinerama.  Rebooted and now the top panel is on the other screen and, more importantly, I can't access the monitor controls anymore.

When I click on Monitors I get an error message that says "Could not get screen informaion, RANDR extension is not present"


I love Ubuntu, but the work required just to get it doing what I need it to do is tough to soldier through.

---

### Post by djaun on 2010-11-21
I feel the same way about Ubuntu. I've also been through your problem several times. The only thing that seems to work is:

1. System > Administration > Additional Drivers
2. Remove proprietary video drivers
3. Reboot
4. Re-install the drivers (I just go to System > Preferences > Appearance and activate visual effects, and let Ubuntu take care of the rest)

Now if I can just figure out why the resolution on my main monitor keeps getting reset to 1024x768. Something to do with the NVIDIA drivers I think, but I can't complain.

---

