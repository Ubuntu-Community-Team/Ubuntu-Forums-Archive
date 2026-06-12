---
title: "[SOLVED] Need to rerun Envy whenever I boot into a different kernel..."
date: 2008-10-19
forum: Multimedia Software
---

### Post by scotty64 on 2008-10-19
I am using different kernels and kernel versions (generic & realtime). The problem is that whenever I boot into a different kernel X starts in low-res mode instead of starting the NVIDIA driver. The only solution is to rerun EnvyNG. But I wonder if there is a way to get the kernelmodule for every kernel installed without having to jump through the hoops of starting Envy, reinstalling the driver and rebooting.

---

### Post by scotty64 on 2008-10-21
I solved the problem of only installing the missing kernelmodule without rerunning Envy by using dkms from the command line. But should not Envy / DKMS do the module installation automatically whenever a new kernel is added to the system ?

---

### Post by markbuntu on 2008-10-21
Not necessarily. If you have neglected to remove old driver kernel modules when you updated the driver the new kernel will not know which modules to load and so will leave them out. 

Many people do this and it has no effect on their system until they get a kernel update.

---

### Post by scotty64 on 2008-10-23
> **markbuntu said:**
> Not necessarily. If you have neglected to remove old driver kernel modules when you updated the driver the new kernel will not know which modules to load and so will leave them out. 

Many people do this and it has no effect on their system until they get a kernel update.

I think that was not the problem. I checked for "leftovers" and I ran "module-assistant prepare" to make sure that the right kernel headers are in the path. It looks more like Envy being unable to manage multiple kernels. I had the impression that whenever I ran Envy to install the driver for one kernel it at first uninstalled all installed Envy NVIDIA drivers and modules (for all installed kernels) and reinstalled them afterwards - but only for the kernel I was working with at that time. I wonder if there is a bug in Envy, or if it would be an improvement to be able to disable this forced driver uninstallation when the driver that is to be installed has the same version number.

---

### Post by markbuntu on 2008-10-23
I never had much luck with envy myself. It always seemed to misinstall the drivers so I don't use it anymore.

---

### Post by scotty64 on 2008-11-08
I could solve the problem at the end by having a detailed look into DKMS and I found two versions of the kernel module there. It looks as there is a bug / missing feature in Envy that does not recognize older module versions correctly and thus causes trouble with DKMS. It should uninstall all old versions instead removing the newly installed one again and again. After deleting the old version and installing the actual version directly via DKMS I have the module in all kernels now.

---

### Post by markbuntu on 2008-11-09
Ahhh, just as I first suspected. Anyway, it is good you got this figured out. 

Could you please mark this thread as solved using the thread tools above.

---

