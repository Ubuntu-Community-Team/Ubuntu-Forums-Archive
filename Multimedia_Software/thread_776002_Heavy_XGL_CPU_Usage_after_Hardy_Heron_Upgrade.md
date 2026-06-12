---
title: "Heavy XGL CPU Usage after Hardy Heron Upgrade"
date: 2008-04-30
forum: Multimedia Software
---

### Post by filosofo on 2008-04-30
Hello all,

I have a AMD 64 3000+ processor and a NVIDIA nForce 3 250 graphics card, and I'm using GNOME.  After upgrading to Ubuntu 8.04 (Hardy Heron) this week, my XGL usage has spiked.  

Compiz effects look the same as before and work smoothly.  I even installed EnvyNG and ran it to see if maybe there was a better NVIDIA driver, but  afterwards there is no difference in CPU usage.

However, instead of typically using 10% of the CPU (as it did under Gutsy Gibbon), Xgl is using at least 40%, even when no desktop applications are running.  This means that if I try to run multiple applications at once, things really slow down.

Any ideas about what I can do to lower CPU usage?

---

### Post by prostar on 2008-05-02
I have a similar issue, and I also noticed that it's only detecting one (out of two) cpus.  I'm starting to gather that this kernel is not that great...

---

### Post by threetimes on 2008-10-08
I also have the same problem, with Compiz turned on, XGL uses between 20%-40%, and with compiz off, usualy below 6%.
That means that with compiz my cpu is about 75°C and without compiz it drops to 55°C and my fans turn off:) (only Opera was running in this test).

I have a 3GHz Pentuim 4 with HT and a Radeon HD 2600XT.

---

### Post by markbuntu on 2008-10-08
If you upgraded to Hardy you need to remove:

xserver-xgl

It conflicts with the drivers for hardy and is no longer necessary to run compiz.

---

