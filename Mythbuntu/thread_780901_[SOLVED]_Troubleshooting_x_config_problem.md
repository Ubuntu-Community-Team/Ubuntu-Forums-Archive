---
title: "[SOLVED] Troubleshooting x config problem"
date: 2008-05-03
forum: Mythbuntu
---

### Post by yonkiman on 2008-05-03
I'm running Mythbuntu Hardy Heron.  When I reboot, I see the progress bar move most of the way to the right.  Then the screen goes black and stays black.  

I then 
- reboot into rescue or diagnostic mode (or whatever it is called)
- tell it to try to fix the x server
- tell it to continue booting
- copy an old, working xorg.conf over the current one,
- launch the restricted drivers manager and re-enable the nvidia driver
- reboot,

and everything comes up great.  But if I reboot AGAIN, I get the black screen and have to repeat everything mentioned above.

It's all very consistent and repeatable.  I'm getting good at these steps.

I'm not sure if the nvidia driver is getting disabled when I reboot and CAUSING the problem, or if the driver is disabled when I boot into diagnostic mode and tell it to fix the xserver.

Does anyone have any tips?  Where should I look for problems?  What logfiles, etc.?

TIA.

---

### Post by superm1 on 2008-05-04
> **yonkiman said:**
> I'm running Mythbuntu Hardy Heron.  When I reboot, I see the progress bar move most of the way to the right.  Then the screen goes black and stays black.  

I then 
- reboot into rescue or diagnostic mode (or whatever it is called)
- tell it to try to fix the x server
- tell it to continue booting
- copy an old, working xorg.conf over the current one,
- launch the restricted drivers manager and re-enable the nvidia driver
- reboot,

and everything comes up great.  But if I reboot AGAIN, I get the black screen and have to repeat everything mentioned above.

It's all very consistent and repeatable.  I'm getting good at these steps.

I'm not sure if the nvidia driver is getting disabled when I reboot and CAUSING the problem, or if the driver is disabled when I boot into diagnostic mode and tell it to fix the xserver.

Does anyone have any tips?  Where should I look for problems?  What logfiles, etc.?

TIA.
After a boot that doesn't work, post /var/log/Xorg.0.log and /var/log/Xorg.0.log.old

---

### Post by yonkiman on 2008-05-05
> **superm1 said:**
> After a boot that doesn't work, post /var/log/Xorg.0.log and /var/log/Xorg.0.log.old

Thanks superm1, you solved the problem.  I didn't actually do anything, it just that you've told me where to look, everything is working fine reboot after reboot.  If it ever fails again I'll heed your advice!

---

