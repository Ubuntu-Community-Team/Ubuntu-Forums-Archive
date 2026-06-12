---
title: "Nvidia drivers mysteriously unconfigure themselves"
date: 2008-06-02
forum: Multimedia Software
---

### Post by ChameleonDave on 2008-06-02
I've set up my girlfriend's computer with Hardy Heron, and made KDE4 the default.  Everything is fine except for the 3D drivers that her NVidia FX5200 needs.

I've tried setting the computer (in "systemsettings") to use the correct "nvidia" driver instead of the crappy "nv" one, but the setting does not survive a reboot.

I've tried using tools such as Envy and Jockey to set it up, and I got the driver working long enough that she could enjoy Compiz.  I think she even rebooted successfully and it still worked.  But this morning, she booted up and there was no more 3D acceleration, leading to a Compiz failure.  Her computer has reverted to "nv" instead of "nvidia".

Why oh why is this happening?  I can't conceive of any possible reason why this should occur.

NB: This is not a question about Compiz; it is about video drivers.

---

### Post by Xiong Chiamiov on 2008-06-02
[Try this.]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")

---

### Post by aeiah on 2008-06-02
is it getting saved to your xorg.conf file? if you're messing with nvidia-settings stuff and havent launched it with sudo, it may not save changes to xorg.

---

### Post by ChameleonDave on 2008-06-02
> **Xiong Chiamiov said:**
> [Try this.]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")
Editing */etc/default/linux-restricted-modules-common* seems to have done the trick, thank you.  Fingers crossed!


> **aeiah said:**
> is it getting saved to your xorg.conf file? if you're messing with nvidia-settings stuff and havent launched it with sudo, it may not save changes to xorg.

If the settings had not been saved, then I never would have got it working in the first place.  I'm not asking how to get it working, but how to keep it working.

---

### Post by aeiah on 2008-06-02
nvidia-settings changes will work for the session without saving to xorg, thats why i asked.

---

### Post by ChameleonDave on 2008-06-04
> **Xiong Chiamiov said:**
> [Try this.]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")

Tried it.  Also tried the suggestion here: [http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

The driver installs OK, everything works fine, I can reboot and it still works.

But them after one or two more reboots, 3d acceleration fails and the /etc/X11/xorg.conf file reverts to how it was.

---

### Post by ChameleonDave on 2008-06-06
OK, I've now tried the EDID trick described at [http://ubuntuforums.org/showthread.php?t=792276#5](http://ubuntuforums.org/showthread.php?t=792276#5), but even then it still doesn't stay configured.

After about three reboots it reverts to crapness.

Somebody please help!  What possible mechanism can be rewriting my *xorg.conf* file?

---

### Post by ChameleonDave on 2008-06-07
I've now upgraded to kernel 2.6.24-19, and everything seemed to be working so quickly and smoothly, with all the 3D acceleration.  I was convinced that the problem had been solved.

But then it failed again.  It was just on a nice long stretch.  We logged on several times before it happened.

I've now resorted to writing a small bash script that restores the* /etc/X11/xorg.conf* to a working version, and I've put a link to it on my girlfriend's desktop, so that she can click on it, hit Ctrl + Alt + Backspace, and log in again with 3D acceleration.

But I want a solution!  What program is it that constantly rewrites my * /etc/X11/xorg.conf* file??  How can I stop this rogue program?

---

