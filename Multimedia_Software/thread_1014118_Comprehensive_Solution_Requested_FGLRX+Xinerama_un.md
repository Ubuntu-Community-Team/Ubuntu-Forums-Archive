---
title: "Comprehensive Solution Requested: FGLRX+Xinerama under Intrepid"
date: 2008-12-17
forum: Multimedia Software
---

### Post by omniuni on 2008-12-17
I would like to start by complimenting AMD. Finally, the FGLRX driver is stable, and works nearly flawlessly. I can even use the Catalyst Control Center to enable Anti-Aliasing and set up a BigDesktop.

Unfortunately, BigDesktop only seems to support two monitors at the SAME resolution! This is somewhat annoying with an LCD that supports significantly higher resolutions than my laptop LCD.

It does seem that FGLRX supports Xinerama, which does handle different resolutions, but in Intrepid xorg.conf doesn't have the entries that I was familiar with on older distributions.

AMDCCCLE does show that the monitors are different, and it shows them supporting different resolutions... but I can't change the resolution of the monitors independently.

So, I would like to enable Xinerama.

I will also note that krandrtray shows just one screen with resolution 2560x800. I have found other people referencing this problem, but I have yet to find a solution that actually looks promising.

Thank you,
Daniel

---

### Post by markbuntu on 2008-12-17
You can set independent resolutions of your displays on big desktop with aticonfig from the command line

aticonfig --help

for a list of options.

---

### Post by omniuni on 2008-12-22
I know about that, but I've not had much success in getting it to work. I have, however, destroyed my X server several times in the process.

Given that Display 2 is my laptop LCD and Display 1 is a Lenovo LCD, and I want:

Laptop | Lenovo

as my setup, and with different resolutions, do you have any more specific suggestion?

Also, I will repeat that I don't think BigDesktop supports different resolutions.

---

### Post by markbuntu on 2008-12-22
In some of the earlier drivers you could drag the monitors around to change them from one to 2 and visa versa but that does not seem to be working anymore. Have you tried the aticonfig
--swap-sceens=on
--swap-monitor

--mode2=

options?

I really do not mess around with my monitors much, they work fine for me with the default setup so I am not sure how helpful I am being here.

---

