---
title: "Getting 720p movies to work on old computer"
date: 2010-05-12
forum: Multimedia Software
---

### Post by topgun_tapan on 2010-05-12
I've a old desktop computer with the following specs
cat /proc/cpuinfo
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 1
model name    : Intel(R) Pentium(R) 4 CPU 1.60GHz
stepping    : 2
cpu MHz        : 1600.011
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips    : 3200.02
clflush size    : 64
power management:

```

cat /proc/meminfo

```
MemTotal:         250852 kB
MemFree:           20140 kB
Buffers:            7312 kB
Cached:            60464 kB
SwapCached:        51320 kB
Active:            72900 kB
Inactive:         128024 kB
Active(anon):      54888 kB
Inactive(anon):    80816 kB
Active(file):      18012 kB
Inactive(file):    47208 kB
Unevictable:           8 kB
Mlocked:               8 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         250852 kB
LowFree:           20140 kB
SwapTotal:        409616 kB
SwapFree:         248032 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        124752 kB
Mapped:            27352 kB
Slab:              11228 kB
SReclaimable:       4192 kB
SUnreclaim:         7036 kB
PageTables:         3000 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      535040 kB
Committed_AS:     780208 kB
VmallocTotal:     766008 kB
VmallocUsed:       35232 kB
VmallocChunk:     726004 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       40896 kB
DirectMap4M:      221184 kB

```

this is the graphics card i have : Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)

I have been able to start 720p videos but with considerable AV drift. When i forward the video the drift temporarily disappears and video starts drifting again. The problem is that the video is always slower than the audio. Framedropping removes the A-V lag but makes the video unwatchable. Any suggestions as to how i will be able to make it work properly ?

---

### Post by hxcobd on 2010-05-12
Have you tried some simple CPU scaling options? The link in my sig has a tutorial on how to do so. I've found that forcing your CPU to scale up can solve a lot of multimedia performance problems.

---

### Post by topgun_tapan on 2010-05-12
> **hxcobd said:**
> Have you tried some simple CPU scaling options? The link in my sig has a tutorial on how to do so. I've found that forcing your CPU to scale up can solve a lot of multimedia performance problems.
I tried that but didnt help. Any other suggestions ?

Also is it possible to ssh to my laptop and use the resources on my laptop to play the file on my desktop or use my laptop in anyway to help play the files smoothly on the desktop ?

---

### Post by cchhrriiss121212 on 2010-05-12
You could try using x11 output. But what player are you using? Smplayer has an av-sync option that might give you watchable video. You could also get a cheap nvidia card and use vdpau, which would handle both 720p and 1080p with that processor.

---

