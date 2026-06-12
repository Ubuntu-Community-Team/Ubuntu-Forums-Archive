---
title: "Accessing 9.04 from 9.10"
date: 2009-12-14
forum: Mythbuntu
---

### Post by NertSkull on 2009-12-14
Ok, so I have a backend setup on my other computer.  I tried upgrading to 9.10 (and thus mythtv .22) and nothing was going right.  So I think I'll just go back to 9.04 where things worked.

But my big question is.  Can I get a front-end on my main desktop, running 9.10, to access the older 9.04 and .21 mythtv.  When I install it on my main desktop I get errors (hence the reason I tried to update the other computer).

Is there a way to do this?  I thought about just installing a .21 front-end on my main desktop, but I didn't get very far that way because I'm no good at compilling source stuff, and .21 is not in the repositories for 9.10.

Can this be done?

---

### Post by klc5555 on 2009-12-14
Everything has to be the same Mythtv version: 0.22 or 0.21 (or 0.20.2 ...) Mixing Mythtv versions will fail (by design) with protocol mismatch errors.

No need for compiling source --the 9.04 binaries for Mythtv 0.21 are generally supposed to install and run on 9.10. 

If all you want to do is enable a 0.21 frontend on a Ubuntu 9.10 desktop, you don't change repositories. Rather use Firefox and download the following two deb packages: mythtv-common and mythtv-frontend, from the "Graphics" section of the Jaunty (9.04) packages at packages.ubuntu.com . Install them with the gdebi installer presumably already linked to Firefox, and you should be OK. 

Assuming this works for you, the two Jaunty packages will then have to be "locked" to keep Update manager from fussing over it.

---

### Post by NertSkull on 2009-12-14
EXCELLENT!!! That worked.  I had to install a few other dependencies as well.  But I now can access the mythtv on my main desktop.

---

### Post by NertSkull on 2009-12-14
How do I "lock" the .21 version in 9.10 to keep it from attempting to upgrade to .22?

---

### Post by nickrout on 2009-12-14
if its working don't change anything!

---

### Post by klc5555 on 2009-12-15
> **NertSkull said:**
> How do I "lock" the .21 version in 9.10 to keep it from attempting to upgrade to .22?

[http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html](http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html)

---

### Post by NertSkull on 2009-12-15
Thanks!!

---

