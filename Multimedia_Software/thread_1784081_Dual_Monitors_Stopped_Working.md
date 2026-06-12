---
title: "Dual Monitors Stopped Working"
date: 2011-06-16
forum: Multimedia Software
---

### Post by mrule on 2011-06-16
Two days ago, the machine worked fine with dual monitors and full hardware accelerated visual effects. Today, my computer has "spontaneously" stopped supporting dual monitors and I have been unable to resolve the issue.

This is quite possibly an NVidia bug, but I will post it here since it is a problem with both Ubuntu and NVidia.

Description :
-- machine works correctly with either monitor alone, including full hardware accelerated visual effects.
-- screen flickers when booting with dual monitors, boots into low graphics mode, screen continues to flicker during use.
-- NVidia config does not detect second monitor when plugged in, or
-- When a second monitor is plugged in, that monitor grabs the screen from the first. NVidia config is then unable to configure graphics at all, as it believes that the first monitor has just vanished, and it does not know that the computer is now displaying on the second monitor. This happens with both monitors in either order.

These are my best guesses as to what has happened :

-- Some update broke or confused the NVidia drivers in some way. This could be due either to an Ubuntu bug that appeared in an update, or a bug in the drivers that only got exposed after an update.

-- Hardware failure on the graphics card or elsewhere is creating problems that only affect dual screen support.


~$ lspci | grep nV                                                             
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

~$ lsmod | grep nv                                                             
nvidia              11980836  40 

~$ cat /etc/lsb-release                                                        
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

any ideas ?

---

### Post by mrule on 2011-06-16
and ... everything is working again.

I changed nothing. 

Just waited for a while and then tried the NVidia settings again. 

This is highly suspicious, possible explanations : 

-- faulty monitor, intermittent.
-- faulty card, intermittent,
-- faulty connections or interference, intermittent.

all causing weird edge cases in the driver to pop up, perhaps ?

---

### Post by santiagoangee on 2011-06-17
Hi.

Man I have a similar problem. One day ago I had two monitors plugged to my laptop ( laptop's monitor and another monitor) and at the startup they ran correctly. but today I start my pc with the two monitors and the desktop freezes. I have tried in every way to solve this problem, getting into the mopnitor's configuration and switching the screen resolutions so the resolutions of both monitors are the same and it seems that neither of this works. Can somebody help me please?

---

### Post by BicyclerBoy on 2011-06-17
The OP was using 10.04 & there has been a kernel update..

Use synaptic package manager & check the update history.

Reboot into GRUB menu & try the previous kernel version.

---

