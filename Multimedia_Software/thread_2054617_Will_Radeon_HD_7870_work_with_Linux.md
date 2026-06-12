---
title: "Will Radeon HD 7870 work with Linux"
date: 2012-09-07
forum: Multimedia Software
---

### Post by thunderpenguin on 2012-09-07
Will Radeon HD 7870 2GB work properly with Linux. Will it run desktop effects and 3d games without any issues?

I will be thankful for any help you give me.

---

### Post by QIII on 2012-09-07
**CAVEAT:  I do not recommend either for or against any purchase.  It is your money and not mine to spend.  You should make an informed decision.**

Phoronix, openbenchmarking and ATI all say it will work.  However, I have not seen definitive results for the 3.X kernels nor have I personally tested that model.  At least one newegg customer has specifically indicated that the Sapphire model works well with Ubuntu.  

ATI has a very close and preferential relationship with Ubuntu in particular among Linux distributions.  If it will work with any, it is most likely to work with Ubuntu.  For several years, the April and October ATI driver releases (or perhaps "pre-releases") have been given to Canonical to be included in the Ubuntu repo before they are available to the general Linux public. (Phoronix boo-hoos and wails about it every time.)   However, it might be wise to use the latest driver rather than 12.4, which is the one found in the Precise repository.  If you choose to try to use 12.4, I would STRONGLY recommend against using the fglrx-updates and fglrx-amdcccle-updates versions (called Post Release Update in the Additional Drivers GUI).  These packages present problems for many users.  

There were a lot of initial problems with the Linux driver when the HD 7XXX series of GPUs first hit the market and ATI really messed up by not having a suitable Linux driver ready for the release of the hardware.  I believe that has been rectified, but you should be aware that it happened.

---

### Post by thunderpenguin on 2012-09-07
Q||| Thank you for your help.

---

### Post by luisspb on 2013-03-09
It's not solved. I've recently acquired a Radeon HD 7870 e it doesn't have a properly 64-bit linux driver that works well. At least, the ones I've tried did not (from Ubuntu, from AMD's website etc.). My Ubuntu version is the 64-bit 12.04.2 Precise Pangolin.
Any news about these issues with the ATI HD 7XXX series?

---

### Post by luisspb on 2013-03-13
WOW! I've finally got it! As incredible as might seem (at least for me), I solved it installing the driver "**experimental** beta", through the Additional Drivers interface, but first I re-installed the Ubuntu (same version, clean install).
It was everything working fine, except for a problem with my monitor, I think, the same one that occurred in Windows, that it wasn't displaying in full screen.
But it was easily solved scaling the output to the monitor through the Catalyst Control Center.

---

