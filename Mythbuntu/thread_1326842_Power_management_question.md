---
title: "Power management question"
date: 2009-11-14
forum: Mythbuntu
---

### Post by sawbuck on 2009-11-14
I've had this issue with a fresh install of Mythbuntu 9.04 and continuing after adding the Ubuntu desktop.  It is a first for ANY installation.

I cannot get the monitor to turn off after whatever time I set in power management.  I've enen tried different screen savers and times although I usually set it up for going to blank screen saver in 5 minutes and powering off in 10 after lapsed idle.  No matter what it continues to stare into the room forever never blinking.

Any ideas anyone?

---

### Post by shawnisalk on 2009-12-03
I have the opposite problem. I want it to stay on no matter what, but it goes blank after ten minutes regardless. *shrug*

---

### Post by shawnisalk on 2009-12-03
I wonder if the solution you are looking for is here...editing xorg.conf

[http://ubuntuforums.org/showthread.php?t=1325308&highlight=power+management+blank+screen](http://ubuntuforums.org/showthread.php?t=1325308&highlight=power+management+blank+screen)

---

### Post by sawbuck on 2009-12-06
Dunno when but the problem seemed to fix itself,  Maybe it was one of the updates.  I seemed to recall a fleeting glimpse of something power related.  Will wait til next time......

---

### Post by shawnisalk on 2009-12-09
Ironically, the xorg.conf suggestion I made worked for me for a little while, then crashed X and corrupted .Xauthority, so I'm back where I started.

---

### Post by sawbuck on 2009-12-11
> **shawnisalk said:**
> Ironically, the xorg.conf suggestion I made worked for me for a little while, then crashed X and corrupted .Xauthority, so I'm back where I started.

I've been tied up with other parts of life but noticed the monitor was again not powering down but - once more for some strange reason - it corrected itself.  I have no clue what's going on but will have to look at the xorg.conf.  

There is an issue I've not had time to sort out that is unrelated this.  I have a conflict between my NVIDIA graphics card and HVR 1600 tuner card that manifests itself in flashing and stuttering during boot and never finishing a boot unless I add a vmalloc=256m to the kernel boot line in grub.cfg.  Once added it will boot fine and operate normally - until the next kernel update which wipes out the edit.  Prior to 9.10, there was a way to make the edit survive the kernel updates.  Just a little pecularity of an open software OS, I guess.

---

### Post by matt06 on 2009-12-11
sawbuck,

Are you using GRUB_CMDLINE_LINUX_DEFAULT to add the vmalloc parameter?  Take a look the [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275") if you haven't already.

---

### Post by sawbuck on 2009-12-17
> **matt06 said:**
> sawbuck,

Are you using GRUB_CMDLINE_LINUX_DEFAULT to add the vmalloc parameter?  Take a look the [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275") if you haven't already.

Matt06,

No, I haven't been using that, I have been editing "grub.cfg" each time the kernel is updated.  I looked at and bookmarked your pointer to the grub 2 guide and will try to implement the suggested optional file. Looks like it would make life easier if I did it right.   But that's for another day....

Thanks for the tip.

---

