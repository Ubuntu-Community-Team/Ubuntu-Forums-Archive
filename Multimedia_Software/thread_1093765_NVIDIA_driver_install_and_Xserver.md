---
title: "NVIDIA driver install and Xserver"
date: 2009-03-11
forum: Multimedia Software
---

### Post by bilijoe on 2009-03-11
OK, I'm in over my head here again. I've tried everything I feel safe trying, and now I'm worried about making things worse, so I decided to stop and ask.;)

I just downloaded a new driver for my NVIDIA GeForce FX5500 (brand new too, dated just a few days ago). It took me forever to figure out how to run a ".run" file (I may be showing how little I know here). When I finally got the command to execute, it ran briefly, then told me to "exit X" (refering to the Xserver), because the install could not run if an Xserver was running. So I booted into recovery mode w/ prompt, and ran it again. This time it told me I was running at level 1, and needed to be at level 3 for the install to work. I copied the command it gave, and executed it, at which point the system booted the rest of the way to the GUI, and, apparently, started the Xserver because when I tried the install again, I got the original message telling me to "exit X".:(

HELP! This can't be as hard as I'm making it. How do I run a shell script (which is what this install is), at level 3, with the Xserver shut down (or unstarted)?:popcorn:

---

### Post by overdrank on 2009-03-11
You may try the command ```
sudo /etc/init.d/gdm stop 
``` Then to return to the GUI after installing then change stop with start in the command.

---

