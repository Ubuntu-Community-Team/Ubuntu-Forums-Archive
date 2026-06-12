---
title: "nvidia module won't load"
date: 2010-07-23
forum: Multimedia Software
---

### Post by mindless18 on 2010-07-23
This nvidia driver is driving me nuts... I have tried everything I can think of including multiple solutions from threads.

I have a GeForce FX5200 with the nvidia-current drivers installed. On boot I receive the following error messages...

FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

If I try and open the nvidia server settings I get the following message.

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

In Jockey I get:

The driver is activated but not currently in use.

I am using headers 2.6.32-23 and have updated to grub2 (something that seems to have fixed a mismatched header issue for others). I have uninstalled and reinstalled drivers, edited the xorg.conf with nvidia-xconfig as well as manually and I don't know what else to do... any suggestions would be appreciated... 640x480 is crap.

---

### Post by ShadowTek on 2010-07-28
I've been having a similar problem with 10.04 after every kernel update. My solution was to reboot into recovery mode and use the GUI to remove and then reactivate the current nvidia driver, which solved the problem.

---

### Post by mindless18 on 2010-07-30
Thanks for the suggestion... I uninstalled nvidia drivers in recovery mode as suggested, but I think what fixed it for me was uninstalling and reinstalling Jockey...

The give away (that I should have acted upon earlier) was that in Jockey, the information about the driver was very limited and I wasn't being "(recommended)" a driver... all is working now... FINALLY!!!

---

