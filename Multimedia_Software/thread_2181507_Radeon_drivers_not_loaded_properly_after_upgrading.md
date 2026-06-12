---
title: "Radeon drivers not loaded properly after upgrading to Saucy"
date: 2013-10-18
forum: Multimedia Software
---

### Post by daniel-arteaga on 2013-10-18
After upgrading to Ubuntu 13.10 (Saucy) in 64 bits, GDM stops to work (strange  colors appearing on screen), and lightdm works using llvmpipe instead of  radeon drivers. Performance is really bad and dual screen no longer  works. It worked perfectly before upgrading.


Output of glxinfo | grep Gallium:
 OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits)



 When loging to the session a message box appears saying "System  program problem detected". Unfortunately when I click to "Send  report..." nothing happens. The display box disappears automatically  after some time.

Apparently there is some problem loading the Xorg module radeon. In the Xorg logs the following message appears:

Failed to load module "radeon" (module does not exist, 0)
Failed to load module "ati" (module does not exist, 0)
Failed to load module "modesetting" (module does not exist, 0)


 However the corresponding kernel module is loaded properly.  'lsmod | grep radeon' shows:


 radeon               1402449  2
ttm                    83995  1 radeon
drm_kms_helper         52651  1 radeon
drm                   296739  3 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon



 Among other things, I tried to purge all radeon-related packages and reinstalling them again, with no success.


 Any idea?

---

### Post by daniel-arteaga on 2013-10-18
I forgot to mention that I filed a bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1240428](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1240428)

---

