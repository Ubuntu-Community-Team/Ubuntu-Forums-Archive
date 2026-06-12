---
title: "PAE upgrade broke Nvidia"
date: 2011-12-13
forum: Multimedia Software
---

### Post by ray field on 2011-12-13
okay, so believe it or not I installed the PAE kernel by accident a few months ago whilst trying to fix VirtualBox on Lucid after a reinstall.  it's fine, I guess -- however every time I install a kernel upgrade from Upgrade Manager, my Nvidia card setup goes kablooey (reverts to VGA with the error screen on bootup).  the last couple of times I've spent a couple of hours getting it back to normal -- this involves searching through various Ubuntu forums and trying out this or that suggested fix until I find some combination that works.  right now I'm back on the last kernel until I can fix this issue.

what in blazes is the problem with these pae kernels blowing up my Nvidia setup every stinking time?

---

### Post by wolfen69 on 2011-12-13
The Nvidia driver requires the DKMS module so it doesn't get blown away every time  there is a kernel update. Check synaptic to see if it is installed.

---

### Post by ray field on 2011-12-14
according to Synaptic the DKMS package is installed, although no other DKMS-related packages have been.

---

