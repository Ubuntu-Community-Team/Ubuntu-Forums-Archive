---
title: "Mythbuntu 8.04 broken on some VIA C3 systems"
date: 2008-05-18
forum: Mythbuntu
---

### Post by ozybushwalker on 2008-05-18
A number of mythbuntu 8.04 applications fail on some VIA C3 CPUs because libmyth includes a CMOV instruction which is unsupported on some C3 CPUs. (It is unsupported on my 800MHz Samuel 2 CPU but supported on my 1GHz Nehemiah CPU.) More detals are in bug 23158 [https://bugs.launchpad.net/bugs/231528]("https://bugs.launchpad.net/bugs/231528")

This will impact anyone doing a clean install or upgrading to Mythbuntu 8.04.

It appears mythbuntu/ubuntu decided (perhaps inadvertently) sometime after the 7.04 Live CD to drop support for the "586 class" CPUs which don't have the CMOV instruction. Unfortunately they appeared to "forget" to tell us. Since Linux is often promoted as an OS for "less well endowed" systems this decision is unfortunate. My C3s use DDR-2 memory and will take at least 512MB so they are not particularly resource constrained nor are they particularly "old" systems.

Here's how to tell if your CPU has the cmov instruction: in file /proc/cpuinfo look for cmov in the flags line: if cmov is there the CPU claims it has a cmov instruction, if cmov is not there the CPU isn't claiming to have the cmov instruction (and therefore probably doesn't).

On my 800MHZ C3 (doesn't support cmov):
```
# grep cmov /proc/cpuinfo
#
```

On my 1GHz C3 (does support cmov):
```
# grep cmov /proc/cpuinfo
flags           : fpu vme de pse tsc msr sx8 sep mtrr pge cmov pat mmx fxsr sse up rng rng_en ace ace_en
#

```

---

### Post by rscott101 on 2008-05-18
Argh. Wish I'd read this post a few hours ago....

Got an Epia M9000 board (the last pre Nehemiah board..). I've spent the last few hours getting it to netboot successfully - it's currently running fc6 and I wanted to test it with Mythbuntu before upgrading.

I guess I'll have to look at getting Mythtv FC8 or FC9 to use XvMC on this, or consider dumping it and getting a newer board with a different processor.

---

### Post by laga on 2008-05-18
There's a PPA with packages for older CPUs somewhere. 

[https://launchpad.net/~jstembridge/+archive](https://launchpad.net/~jstembridge/+archive) - darn, only for Gutsy :( Maybe they'll work anyways.

We'll try to find a solution for the CMOV problem. An official solution will probably only happen for Intrepid because it's a bit hard to introduce such changes in a stable release.

Regards,

laga (annoyed at VIA for making weird CPUs)

---

### Post by ozybushwalker on 2008-05-19
> **laga said:**
> 
We'll try to find a solution for the CMOV problem. An official solution will probably only happen for Intrepid because it's a bit hard to introduce such changes in a stable release.



I have a number of questions:

What CPUs are supported by Mythbuntu?

Making an official solution to this CMOV problem available only on a release after 8.04 effectively means the C3 CPUS without CMOV are unsupported in 8.04. Yet, one could reasonably believe they were supported in 7.10. I don't recall seeing any notice of change in support status. Is it Mythbuntu policy that dropping support of "older" hardware does not require announcement and does not require consultation with the user community?

If such consultation and/or announcement is required by policy, where will such consultation or announcement take place?

Will Mythbuntu include in future releases and updates a mechanism to inform the end users if an attempt is made to run the software on a CPU which lacks the necessary support? (I spent many hours investigating and trying to find workarounds for this and other problems. I'm trying hard to not be annoyed at mythbuntu/ubuntu for 'forgetting' to tell me the build options had changed so mythbuntu would no longer work on "older" C3 CPUs. :) )

---

### Post by Jens Svalgaard on 2008-09-23
I've created a PPA with mythtv compiled for the VIA C3 cpu with the missing CMOV instruction:

   [https://launchpad.net/~jens-ubuntu-svalgaard/+archive](https://launchpad.net/~jens-ubuntu-svalgaard/+archive)

So far, I've only tested this on a mythtv-backend, but it should work for a frontend as well. :)

---

