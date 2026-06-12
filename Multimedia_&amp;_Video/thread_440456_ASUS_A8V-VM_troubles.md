---
title: "ASUS A8V-VM troubles"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by glenngds on 2007-05-11
I bought this motherboard 2 months ago.  The sound has a high pitched squeal that occurs only in Linux.  The graphics are so slow that a computer of 1/3 the speed blows it away as far as graphics go.  For instance with Google Earth and the game gl-117 a 1200Mhz Pentium 3 with integrated intel graphics blows away my AMD 64 3800+ processor.  

Anyway here is the result of cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3800+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 2001.33
clflush size    : 64

Is there any more info needed for someone to figure out why my graphics is so slow on my new computer?

---

### Post by glenngds on 2007-05-11
I think I found the answer to my problems.  I just downloaded sysinfo and checked what it said about my system--in almost every category the specific item on my motherboard was classified as unknown--that includes IDE bus, PCI bus, Video, Audio, memory controler, interupt controller, etc. and etc.  I just discovered some Linux drivers on the CD disk that came with the Motherboard.

---

### Post by glenngds on 2007-05-11
the drivers come as source code and will not compile on my system.  I am uploading the source code and I just hope some can get it to someone that can help.  no drivers were included for the video

---

