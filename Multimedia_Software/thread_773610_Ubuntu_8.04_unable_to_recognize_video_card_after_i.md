---
title: "Ubuntu 8.04 unable to recognize video card after installing driver"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Anonymoose on 2008-04-29
Hi, I'm new to linux, and got Ubuntu up and running for only a couple days now. I'm starting to like it, but one thing that's been bugging me is that ever since I've installed my NVIDIA driver; which worked just fine, so it seemed; it'd not recognize it when I reboot. I get to the splash screen and then some text saying something along the lines of: "running anacron" (I think) and a few other things and then the prompt telling me to run in low graphics mode. I've so far resorted to just reinstalling the driver every reboot. 

I have an NVIDIA GeForce 6100 nForce 405 and the driver I'm using is "NVIDIA-Linux-x86-169.12-pkg1.run". I'm honestly not really sure if this is the right or the most up to date driver, and I've been a little confused by what I've gotten out of google trying to verify that...

---

### Post by Anonymoose on 2008-04-29
Just tried using Envy, and I still have the same problem. Does anybody have any suggestions?

---

### Post by litmos95 on 2008-04-29
Why didn't you use the restricted driver from ubuntu, it is as good as the one from NVidia if not better.

---

### Post by windreiter on 2008-04-29
Same problem here. Both the manually installed driver and the driver from restricted modules don't work. There was no difference if the driver was installed via EnvyNG or by downloading the driver from the nvidia-website.

After a reboot I always got the low graphics prompt. The only driver that worked was the "nv" driver.

I upgraded from Gutsy during beta-testing-phase. The nvidia-glx-new worked from there until final version of Hardy. But because of a another graphics-problem (see launchpad-entry [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220951](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220951)), I tried several drivers and had to uninstall nvidia-glx-new. From there it didn't worked any more after reinstalling.
It seems to be a problem with the 2.6.24-16 kernel. I've given up and run the realtime kernel now. nvidia-glx-new is working again but still with the problems described in launchpad.

Greetings from Germany.

---

### Post by Anonymoose on 2008-05-02
Bumping this in the hope of getting a fix, I'm still stumped

---

