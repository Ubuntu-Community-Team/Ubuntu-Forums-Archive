---
title: "Dell Inspiron i8500 and eclipse &quot;queueing viewer updates&quot;?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by FlyingDoug on 2006-08-27
I've been using my Dell Inspiron i8500 laptop for a few years with Fedora without problems.  I recently decided to try Kubuntu and installed it last week (Dapper).  I'm doing some Java development with Eclipse and a new popup now regularly appears that says "Queueing viewer updates" after I do some editing.

I'm guessing that is a X driver performance issue but I'm not certain.  I couldn't find anyone else mentioning the same popup msg so I thought I'd ask here.  I have not installed NVidia drivers and am wondering if I should or not.  I didn't want to install them if it wasn't really necessary.  I'd appreciate any thoughts on if I should ignore this or do something about it.  I do notice that my fan(s) seem to be on more often than before now.  I recently replaced my Dell TrueMobile 1300 wireless card with an Intel 2915 (works much more easily now) but I'm not sure if that is making the system warmer or not.  GKrellm says the temperature is usually 50c (and I'm not sure if that is good or not).

Some details about my system config:

X Window System Version 7.0.0
Release Date: 21 December 2005

Device "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"

# uname -a
Linux laptop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz
stepping        : 7
cpu MHz         : 1994.412
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid
bogomips        : 3992.80

# cat /proc/meminfo
MemTotal:      1035840 kB
MemFree:         82472 kB

---

