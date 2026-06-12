---
title: "Reinstalling NVIDIA proprietary drivers post kernel upgrade?"
date: 2011-01-13
forum: Multimedia Software
---

### Post by laeg_ on 2011-01-13
A WINE guide for improving performance of World of Warcraft stipulates that post my upgrade to Ubuntu 10.10 I should reinstall my proprietary NVIDIA drivers.

So far in my attempt to do this I have searched synaptic package manager for nvidia, and marked all the resulting installed packages for installation. 

Will this do it or is there something else, or a better way to do this?

---

### Post by wkulecz on 2011-01-13
Unless its changed for no reason in 10.10, the System->Administration->Hardware Drivers main menu selection should do the trick and set things up so the drivers get updated with kernel automatic updates.  I just redid this on 10.04 to recover from an automatic update gone bad.

If you are using a custom kernel from outside the repos, all bets are off!

---

### Post by laeg_ on 2011-01-13
> **wkulecz said:**
> Unless its changed for no reason in 10.10, the System->Administration->Hardware Drivers main menu selection should do the trick and set things up so the drivers get updated with kernel automatic updates.  I just redid this on 10.04 to recover from an automatic update gone bad.

If you are using a custom kernel from outside the repos, all bets are off!

Customer kernels from outside of the repos is something I have yet to tackle and will leave on the long finger for now at least :)

Hardware Drivers is not in System >> Admin >>, perhaps what you're looking for can be found in System >> Admin >> Alternative Drivers? Although that said there does not seem to be many options in there at all.

So to clarify, where should I be going and how do I set the drivers up to update with each kernel upgrade?

---

