---
title: "NVidia API Mismatch"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by cdkorzen on 2008-03-29
Hello:

Let me pre-empt, I HAVE followed tseliot's guide to NVIDIA drivers, and searched about proper installation.

My situation:

I have a GeForce4 Ti 4600.  Kernel version 2.6.22-14, Kubuntu version 7.10.

After booting up after being unable to do so for a while, KDM failed and I was dumped to a text-login.  Whenever I tried to start X, I was told there was an API mismatch.

I have run "sudo apt-get update" and "sudo apt-get upgrade" to make sure my installed packages are up to date.  I have tried both nvidia-glx and nvidia-glx-new.  My card is in the supported list.

I have tried installing the 171.06, 1.0-9755, and 1.0-9631 drivers from NVidia's site.  The 9755 installer says my card is not supported, both 171.06 and 9631 will install just fine.  After the installation, I can start x and KDE comes up just fine.

Then I restart, and I get the API Mismatch error again.  It seems that I have not fixed the issue.  My xorg.conf file has a line for the "nvidia" driver, and "dri" and "GLcore" are commented out.


I fear it's probably something stupid, but I can't find the solution.  Has anyone encountered this?  Does anyone know the solution?

---

### Post by cdkorzen on 2008-03-31
Anyone?  I really don't want to be forced to totally reinstall the OS, but that's the only thing I can try.  I HAVE tried these guides, and it's a shock to me that it's not working, because like I said, it WAS working before :(

---

