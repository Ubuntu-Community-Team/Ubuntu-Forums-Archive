---
title: "Upgrade from 11.10 to 12.04 seems to be hung"
date: 2013-03-26
forum: Mythbuntu
---

### Post by bpmod on 2013-03-26
I am setting up a brand new combined frontend/backend to use at my mother's house, so I have assembled the following:

Mobo: Asus P8B75-M/CSM
CPU: Pentium G630 (2 cores 2.7GHz)
RAM: 8GB (Corsair DDR3)
GPU: Asus Nvidia Geforce GT610 (2 GB)
HD: Seagate Barracuda 2TB
Tuner: Hauppauge HVR 1250

I installed Mythbuntu from my 11.10 CD because I thought it would be quicker.

Installation went perfectly. No issues. Upon booting, I was met with two windows before the interface went to the frontend. I closed the frontend, and also the Update Manager, leaving me with the "12.04 is available" window. I clicked upgrade and waited.

Within about 20 minutes or so, it had progressed through
Preparing to upgrade
Setting new software channels
Getting new packages

and to
Installing the upgrades

where it has sat now for 16 hours.

How can I tell what it is doing and set it on its way again?

Thanks

Brian

---

### Post by AlecJ on 2013-03-27
If this was me and as it's a new install with nothing to lose.
I would reboot and then start update manager again after reboot.

---

### Post by donb21 on 2013-03-30
I've had similar experiences when selecting the option to install upgrades during the installation; I'm not sure I've ever seen it complete successfully on my systems during installation.  I do lots of experimenting, so always assumed it was something I've done.  I've gotten into the habit of selecting default settings during installation.  If it has to retrieve something, I don't select it.  After the installation completes, then I run updates (whatever the software manager recommends, nvidia drivers, etc.).

I've also noticed that the software manager tends to hang during updates when the updates contain anything about the kernel...maybe that's a clue.  It generally recovers after a reboot and re-run of the update, but if done during installation, maybe it doesn't have enough to recover with.  The recovery only seems to work if the upgrade was done after a "default" installation...not if done during the installation.  If it fails during an installation, I generally start over (not sure what I missed...better safe than sorry).
 
Of course, this is all conjecture on my part...just my personal experience.

---

