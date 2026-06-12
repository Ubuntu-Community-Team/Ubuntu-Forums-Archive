---
title: "Hardy just won't work with nvidia Geforce 9500 GT"
date: 2009-06-02
forum: Multimedia Software
---

### Post by jozxyqk on 2009-06-02
I am having trouble getting my Geforce 9500 GT card working with the nvidia proprietary drivers under Hardy Heron.
I have tried:
1) installing nvidia-glx-new driver.  No go.  It boots into "low graphics mode"
2) uninstalling all nvidia packages, installing envyng and making sure pci.ids is up to date.
No go.  envyng says it can't autodetect my card.
3) Installing directly from Nvidia's site and following all instructions from their setup process.  The process says it succeeds, but the machine boots into "low graphics mode".
 
My card shows up like this under lspci:
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

The only thing that I can think of that is relevant is that my motherboard has an on-board video adapter, but I'm not using it. 

Any more suggestions?
Any more information I can supply to the experts for help?
Or, will an upgrade to Intrepid Ibex (or JJ) make this "just work"?
That's my next thing to try if no more suggestions help.

Thank you.

---

### Post by jozxyqk on 2009-06-04
After upgrading to Intrepid Ibex as a last-ditch effort, still having video problems, and finally looking at the failsafe logs, I got some other terms to search for.

And it led me to this explanation which makes perfect sense for my situation:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926)

Hopefully I can assist anyone who ends up doing similar Google searches to me.

But the end solution is that I'm going to have to reinstall from scratch, with the 64-bit flavor of Ubuntu.

---

