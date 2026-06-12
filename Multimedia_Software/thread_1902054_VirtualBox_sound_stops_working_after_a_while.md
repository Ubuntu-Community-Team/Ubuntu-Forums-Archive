---
title: "VirtualBox sound stops working after a while"
date: 2011-12-29
forum: Multimedia Software
---

### Post by eckscalibur on 2011-12-29
I have a Windows XP guest which I run through VirtualBox.  Until recently, everything has worked flawlessly; however, after updating something (either the guest additions or the software itself), sound will stop working randomly after running for a while.  Note that this is isolated to the guest system only, and a restart of the guest will fix the problem.

---

### Post by collisionystm on 2011-12-29
> **eckscalibur said:**
> I have a Windows XP guest which I run through VirtualBox.  Until recently, everything has worked flawlessly; however, after updating something (either the guest additions or the software itself), sound will stop working randomly after running for a while.  Note that this is isolated to the guest system only, and a restart of the guest will fix the problem.

Have you re-installed the guest additions?

---

### Post by eckscalibur on 2011-12-29
Thanks!  That worked.

EDIT:  It seemed to work for a while, but it's stopped working again. :(

---

### Post by schleppel on 2012-01-17
I have this problem as well.
Sometimes the sound comes back without a restart of the guest and then it sounds like 20 sounds or so are played back simultaniously.

---

### Post by ergosteur on 2012-05-30
Same here, VirtualBox 4.1.16 on 12.04 .. Running with PulseAudio on Kubuntu.

---

