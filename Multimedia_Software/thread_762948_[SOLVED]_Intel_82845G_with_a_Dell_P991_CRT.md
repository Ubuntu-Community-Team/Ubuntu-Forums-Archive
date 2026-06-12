---
title: "[SOLVED] Intel 82845G with a Dell P991 CRT"
date: 2008-04-22
forum: Multimedia Software
---

### Post by robelliott2125 on 2008-04-22
Hi all,

I did post this previously, so it is archived, however there were no responses, and since my XP Partition has become screwed, i've decided to take the giant leap to my Ubuntu, and as long as I know how to solve all my problems, I'll be 100% happy.

> 
I'm a complete n00b, on the ubuntu front, and have taken sometime trying to seriously solve this by myself along with other people, but nothings working, so hoping someone here can help.

I'm running an Intel 82845G Gfx card, which is onboard, with a Dell P991 monitor.

Within windows, I'm able to push the monitor to 1280 / 1024 with 75hz refresh, and looking for this in Ubuntu.

Ubuntu finds the monitor with no probs, and thus far I've not seen any errors with the gfx card.
However, when changing to 1280 / 1024 with 75hz, nothing happens, even after a restart or ctrl + alt and backspace.

If i change to 85hz, the monitor goes completely blank, doesn't revert back to the old settings, and seems to completely die on me, causing me to hard reboot the system, which then comes up with some sort of problem, which as yet i've not figured how to resolve, forcing me to reinstall.

The reinstall isn't a prob, as i'm new to ubuntu, but trying to learn how to solve all my problems.

Most have been solved through friends which is good, but this, nobody seems to be able to help with.

Let me know if theres anything you need to know, or have copied.

Thank you!!!

Thanks in advance!!!

---

### Post by robelliott2125 on 2008-04-23
Any help anyone???

If theres any info you need, please let me know!!!

I'm now completely without windows, and i'm really wanting to get my ubuntu just running at the right refresh rate and resolution.

Thank you,

---

### Post by robelliott2125 on 2008-04-23
> **robelliott2125 said:**
> Any help anyone???

If theres any info you need, please let me know!!!

I'm now completely without windows, and i'm really wanting to get my ubuntu just running at the right refresh rate and resolution.

Thank you,

Managed to solve this myself, by using the i810 intel driver, the minute it restarted, that was it, 1280/1028 with 75hz refresh.

Verrrry happy!!!

---

### Post by robelliott2125 on 2008-08-19
Sorry to bring this back up, but i've now just upgraded to Hardy, and now can't figure out how to change my Card / Res / Ref rates.

Any help would be appreciated...

Thanks.

---

### Post by robelliott2125 on 2008-08-19
Anyone?

---

### Post by robelliott2125 on 2008-08-19
Anyone know how to change the refresh / resolution within Hardy for my card?

My screen should be 1280 / 1028, with 75hz refresh, if that helps.

---

### Post by robelliott2125 on 2008-08-20
Anyone???  I would like to have a decent refresh / resolution for my monitor...

I don't know how to do that xconf thing, else i would try that.

Thank you,

---

### Post by robelliott2125 on 2008-08-20
Once again, I've managed to solve this...

Thanks to the guys in IRC.

```
gksudo displayconfig-gtk
``` allowed me to select the correct graphics card, my monitor, along with the refresh and resolution settings.

The above should help anyone else who has this problem.

---

