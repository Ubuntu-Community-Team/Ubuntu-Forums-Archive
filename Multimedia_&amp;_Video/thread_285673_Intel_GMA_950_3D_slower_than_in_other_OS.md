---
title: "Intel GMA 950 3D slower than in other OS"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by kmARC on 2006-10-27
Hi all,

I have an intel centrino core duo laptop at 1.83GHz, equipped with intel GMA 950. 

My problem is that:
**[kmarc][gilgamesh][~][$] glxgears -printfps**
[COLOR="Red"]libGL warning: 3D driver claims to not support visual 0x5b[/COLOR]
4338 frames in 5.0 seconds = 867.580 FPS
4519 frames in 5.0 seconds = 903.620 FPS
4521 frames in 5.0 seconds = 904.139 FPS
4537 frames in 5.0 seconds = 907.222 FPS
4537 frames in 5.0 seconds = 907.220 FPS

So, first of all, what does the line with the warning-blabla mean?
Secondly, ~900 FPS seems too slim, as it is double for example in Gentoo (there I get ~1600-1700 FPS)

Some informations:
**[kmarc][gilgamesh][~][$] uname -a**
Linux gilgamesh 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

**[kmarc][gilgamesh][~][$] cat /proc/cpuinfo**
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
[COLOR="Red"]bogomips        : 3662.51[/COLOR]

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
[COLOR="Red"]bogomips        : 3657.75[/COLOR]

(khm... bogomipses in gentoo is also the double of these measures...)
(and before the questions, no, it doesn't help me if I raise the frequency with cpufreq-set... ;-) )

**[kmarc][gilgamesh][~][$] lsmod**
[...]
i915                   21632  2
drm                    74644  3 i915
agpgart                34888  3 drm,intel_agp
[...]

**[kmarc][gilgamesh][~][$] glxinfo | grep direct**
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes


Oh, and I also have thebeerorkid-aixgl repository, so my mesa, drm, whatever packages are the latest. As I know...

So, what to do, with these bad "performance" values?

---

### Post by amborle on 2006-11-26
I have the same graphics card and drivers but even lower fps (around 700).

Need help too...

---

### Post by kmARC on 2006-11-26
Oh, I'm just wondering this topic being still alive...

I experienced that Beryl runs smoothly but e.g. mplayer cannot play movies while multiple windows are opened (with beryl of course).

So, thank you this UP, keep waiting for solving... :-?

---

### Post by zgornel on 2006-11-26
I have around 980fps on my i915 with recompiled Mesa 6.5.1. Performace of the intel video drivers in poor, I hope this issue will be fixed somehow in the future. There is quite a number of laptops that have the intel extreme 'low performance' graphics.

---

### Post by Tilex on 2006-11-26
```
alex@localhost:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x5b
5878 frames in 5.0 seconds = 1175.572 FPS
19208 frames in 5.0 seconds = 3841.484 FPS
14145 frames in 5.0 seconds = 2828.881 FPS
19013 frames in 5.0 seconds = 3802.536 FPS
19234 frames in 5.0 seconds = 3828.207 FPS
15929 frames in 5.0 seconds = 3185.220 FPS

```
I have the same intel chipset graphics card and these are my FPS rates.  I just intalled Edgy and I didn't tweak anything...maybe you guys should upgrade to Edgy for better video support?

---

### Post by zgornel on 2006-11-27
Do you have a i915 or a i950? I think those results are a bit too high for a 915 ... :rolleyes:

---

### Post by Tilex on 2006-11-27
I have i915.
```

alex@...:~$ lsmod
Module                  Size  Used by
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  10
i915                   21632  2
drm                    74644  3 i915
.....

```

---

### Post by zgornel on 2006-11-27
Hmm... Could you post your system specs ? I never got over 1200 fps on dapper or edgy no matter what I did. Plus, 1000fps range is reported by most users ... Try doing a *lspci | grep Display*, to be sure, kernel modules do not convince :D

---

### Post by Tilex on 2006-11-29
There you go!  If you find why my FPS are that high..tell me why!  I looked on Intel's website and they seem to have a new driver.  Do you think it would help to install that new driver for a i915 on Edgy?

```
alex@...:~$ lspci | grep Display
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

```

---

### Post by zgornel on 2006-11-29
Hmm. Mine is a ```
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

``` Seems to like the only difference is the revision and the 04 revision has higher performance... Anyway, you could recompile libdrm and Mesa 6.5.1 or improved performance. As for the intel drivers ... leave them.

---

### Post by Siegfried on 2007-03-09
> **zgornel said:**
> Hmm. Mine is a ```
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

``` Seems to like the only difference is the revision and the 04 revision has higher performance...
Is it really true that just one revision later the card is 3-4x faster?  Maybe it's a desktop card vs mobile?

---

### Post by zgornel on 2007-03-11
It should not be a great difference between mobile and desktop, the chipsets are identical and memory/hdd performance should not count in glxgears. I can't imagine where that difference came from :D

---

### Post by Siegfried on 2007-03-14
> **zgornel said:**
> It should not be a great difference between mobile and desktop, the chipsets are identical and memory/hdd performance should not count in glxgears. I can't imagine where that difference came from :D
The clock speed of the desktop version is much higher than the mobile version.

---

### Post by Kozodoj on 2007-03-31
I think that the answer is simple. The window with glxgears was under another window... There are sample results from my latop:

3884 frames in 5.0 seconds = 776.696 FPS
4789 frames in 5.0 seconds = 957.778 FPS
4787 frames in 5.0 seconds = 957.230 FPS
2514 frames in 5.0 seconds = 502.155 FPS
2223 frames in 5.0 seconds = 444.396 FPS
3905 frames in 5.0 seconds = 780.961 FPS
4502 frames in 5.0 seconds = 900.284 FPS
4793 frames in 5.0 seconds = 958.464 FPS
4742 frames in 5.0 seconds = 948.394 FPS
20248 frames in 5.0 seconds = 4049.552 FPS
13191 frames in 5.0 seconds = 2638.079 FPS
15208 frames in 5.0 seconds = 3041.523 FPS
14239 frames in 5.0 seconds = 2847.753 FPS
12846 frames in 5.0 seconds = 2569.104 FPS

During the test I turned off Compiz, then covered the whole screen with Firefox window. I must say that with OpenSuse I get almost twice more fps than in Ubuntu.

---

### Post by ysse on 2007-04-04
Hi,
just some additional data to confirm. Dapper was much faster. Edgy and Feisty is a disappointment with respect to Intel GMA 950 performance.'
BTW, does anyone know which package the i915 module is in?

Feisty:
ysse@anders:~/nwn$ uname -a
Linux anders 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux


ysse@anders:~/nwn$ lspci |grep Display
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

snip from /proc/cpuinfo
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz

ysse@anders:~/nwn$ glxgears
4413 frames in 5.0 seconds = 882.490 FPS
4444 frames in 5.0 seconds = 888.785 FPS
4434 frames in 5.0 seconds = 886.618 FPS

Dapper was about 1700 fps:

ysse@anders:~$ uname -a
Linux anders 2.6.15-28-686 #1 SMP PREEMPT Thu Feb 1 16:14:07 UTC 2007 i686 GNU/Linux
ysse@anders:~$ lspci |grep Display
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)

ysse@anders:~$ glxgears -printfps
8531 frames in 5.0 seconds = 1706.089 FPS
8559 frames in 5.0 seconds = 1711.626 FPS
8562 frames in 5.0 seconds = 1712.379 FPS

---

### Post by Siegfried on 2007-04-05
> **ysse said:**
> Hi,
just some additional data to confirm. Dapper was much faster. Edgy and Feisty is a disappointment with respect to Intel GMA 950 performance.'
Yes, I notice the performance drop as well, Dapper was about twice as fast.  There is something sketchy with Edgy...

---

