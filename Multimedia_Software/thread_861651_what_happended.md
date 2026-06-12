---
title: "what happended?"
date: 2008-07-16
forum: Multimedia Software
---

### Post by jaw1959 on 2008-07-16
I just installed a new update, which included a new kernel and such (I'm running 8.04 x86_64 on a Pentium D cpu), and when I restarted, suddenly, my video and audio drivers stopped working. I have been running fine for months on the latest install, and nothing has changed as far as my hardware goes, but now my nvida 7900gt and my soundblaster live both stopped working.  Has anyone else seen anything similar?

---

### Post by jaw1959 on 2008-07-16
is there any reasonable way to undo the installation of the last set of updates so I can go back to my last working configuration?

---

### Post by Cone on 2008-07-17
At boot-up can you pick the non-topmost kernel in the grub list and see if that works (as far as going to your last configuration)?

My guess for the graphics breaking would be a non-updated restricted-modules, and I don't have a clue about the sound unless you compiled alsa yourself because you have a new card only supported in 1.0.17, in which case just doing that again (./configure, make, sudo make install) will fix it (I had this problem).

If you installed the graphics driver via Nvidia's site and downloading their script, you'll need to run that again to reconfigure against the new kernel.

---

### Post by jaw1959 on 2008-07-17
No,  haven't compiled any of my drivers, everything has been from the repo's all the way.  I'm not sure what happend, as I've had problems with this system, and a mythtv server that I run.  I tried running the previous version, but that seems to have no effect (I'm using the lilo boot loader, which gives me the choice of starting "linux" or "old linux").  I'm just going to give up and reinstall.  I have my systems setup to do that rather quickly anyway.  

Thanks, and thanks to all those that tell me what I could have done to fix this easily the second after I begin to reinstall.  

Josh

---

### Post by xc3RnbFO8P on 2008-07-17
> Thanks, and thanks to all those that tell me what I could have done to fix this easily the second after I begin to reinstall. 
I would reinstall if I was you (32 bit).

---

