---
title: "Wireless slow...when is a new kernel 2.6.28?"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by gpenguin on 2008-12-09
I have an HP G60-123CL with an Atheros AR928x wireless card using the ath9k driver.  It seems there is an issue that results in a very slow speed.  My network is a 'g' which is 54MB/s but I'm running at only 1MB/s.

I found [this bug]("http://bugzilla.kernel.org/show_bug.cgi?id=12093") which says to patch the kernel or wait for the 2.6.28 kernel to come out in XUbuntu.  Any idea when that will be?

---

### Post by ajmorris on 2008-12-11
hi there,
the 28 kernels have been pushed out to the jaunty repos... So you *could* update to jaunty to get the kernel, but if you do that, remember, there is a reason why they are development releases... the 28 kernel is only a pre-release version, and is still buggy, but you could also get the kernel source from kernel.org and either compile your own kernel, use the 'genkernel' application, or use the .config file from the 27 intrepid kernel headers.  As for when the 28 kernel will be released not as a development version, i could not say...


AJ

---

