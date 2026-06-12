---
title: "ATI Raedon 9800 Pro Installation Questions"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by Darrin on 2005-11-12
Im still having a little issues with it.
I went to Synaptic and installed xorg-driver-fglrx. I also noticed there was xorg-driver-fglrx-dev. Do I need to install that one also?
According to [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver")    Step 3 im not sure about if I have a nforce2 based mobo. I use an asus mobo cant remember the model. Should I just skip step 3 and assume Im done?

---

### Post by mlomker on 2005-11-12
Look at my [how-to]("http://ubuntuforums.org/showthread.php?p=408111") and let me know if you have any problems.

---

### Post by DJ_Max on 2005-11-12
Do a
```
cat /proc/cpuinfo
```

---

### Post by Darrin on 2005-11-12
[QUOTE=DJ_Max]Do a
```
cat /proc/cpuinfo
```[/QUOTE]

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Athlon(TM) XP 2100+
stepping        : 1
cpu MHz         : 2159.043
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 4276.22

```

Im assuming I dont have it? Dont really know what Im reading here.

---

### Post by Darrin on 2005-11-12
Looks like I got it working. I tested it on planetpenguin-racer game. Before it was almost at a crawl. [Now doing these steps.]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver") Its running great. :) 
Thanks

---

