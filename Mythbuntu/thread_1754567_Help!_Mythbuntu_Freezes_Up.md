---
title: "Help! Mythbuntu Freezes Up"
date: 2011-05-10
forum: Mythbuntu
---

### Post by martynh on 2011-05-10
I've had mythbuntu (currently 8.10) running happily for a couple of years now, then suddenly last night the front end froze up on me. I couldn't even ctrl-alt-backspace or alt-tab although the mouse cursor still moved. On reboot the same thing happened, it automatically launched myth but freezes on pre-scaling images. 

I disabled the automatic launching of myth but even opening a settings window in ubuntu causes the hang. 

After many reboots and much trawling of forums I decided to do a fresh install of 10.10, but get exactly the same behaviour. As soon as I open anything (even a settings window) it freezes, although the mouse cursor is still active and I can remote in using putty. The weird thing is the actual myth installation ran fine?

I have pastebin'd my [_dmesg_]("http://pastebin.com/LmhvNCL5"), and [_Xorg.0.log_]("http://pastebin.com/isuXpZzp") if that helps. Any ideas?

---

### Post by klc5555 on 2011-05-10
When a machine has been working for a long time and then, without any modifications or changes, stops working, I tend to suspect hardware rather than software. 

Hardware failures tend to cluster around heat and motion, so non- functioning or dust-bunnied-up CPU and GPU fans and heat sinks could be causing their components to get a bit hot and error under load (like when X starts). They would need to be cleaned. Heat creep could be causing your video card to unseat itself a bit from the slot, and it would need to be reseated. 

Very common is that a power supply could be just beginning to fall out of spec prior to failing completely, and is giving errors that look like memory hangs under added load, like when X starts. GPU memory or a main-memory DIMM or SIMM could be failing, though this is unusual in a system that has been stable for a long time. On older motherboards, the voltage regulation and supply circuitry could be getting a bit dicey prior to failing.

At any rate, I'd start checking out the hardware. Good luck.

---

### Post by martynh on 2011-05-11
Thanks, I guess hardware is a likely candidate although weird how it could run all the installation steps quite happily. Oh well I have bought a new mobo/cpu/ram so I'll see how it goes :/

---

### Post by klc5555 on 2011-05-11
OK, but don't forget to be suspicious of the power supply. In particular the cheap power supplies sold bundled with cases are more much likely to fail at around the two year point than any of the solid-state items like memory, cpu, etc. are.

---

### Post by nickrout on 2011-05-12
unfortunately the only way to test these things is swapping them min and out.

Although the first step should be a thorough run on memtest86 (available on most linux live cds). By thorough I mean a day or so...

---

### Post by martynh on 2011-05-12
> **klc5555 said:**
> OK, but don't forget to be suspicious of the power supply. In particular the cheap power supplies sold bundled with cases are more much likely to fail at around the two year point than any of the solid-state items like memory, cpu, etc. are.

Hmm, Power Supply is four years old but it's a Seasonic so I would hope it's still ok... 

The new install is pretty much up and running (just got to play with nvidia settings to get native TV resolution) so the family are happy at least :)

---

