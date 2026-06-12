---
title: "Ubuntu Kernel Related Questions"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Nullack on 2010-09-02
Just curious about some kernel related stuff I see:

Sep  3 10:29:10 Bizmark kernel: [    0.000000] SMP: Allowing 24 CPUs, 8 hotplug CPUs
Sep  3 10:29:10 Bizmark kernel: [    2.974400] Brought up 16 CPUs
Sep  3 10:29:10 Bizmark kernel: [    2.974402] Total of 16 processors activated (121601.43 BogoMIPS).

Q1: Is it that the Ubuntu desktop kernel allows up to 24 logical CPUs and 8 hotplug physical CPUs

Sep  3 10:29:10 Bizmark kernel: [    0.010000] Detected 3799.588 MHz processor.

Q2: Does the kernel support Intel turbo mode? I should be hitting a mult of x20 and not the non turbo of x19, and given my BCLK is 200mhz that should be 4GHz. Instead it's reporting non turbo of 3.8ghz.

How do I tell the *REAL* CPU speed, and see what the MULT actually is?

Many thanks

---

