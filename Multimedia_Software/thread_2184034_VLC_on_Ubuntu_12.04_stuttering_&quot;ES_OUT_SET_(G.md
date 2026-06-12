---
title: "VLC on Ubuntu 12.04 stuttering: &quot;ES_OUT_SET_(GROUP_)PCR  is called too late&quot;"
date: 2013-10-27
forum: Multimedia Software
---

### Post by elo96 on 2013-10-27
I'm finding that when playing a DVD on Ubuntu 12.04 using VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b) that the dvd freezes every few minutes for a few seconds. When it happens the error log reads
```

[0xb5300618] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to *** ms)

```

I've ensured that GPU accelerated decoding is enabled as suggested by a thread with a similar problem, but no joy. Would anyone be able to give me advice on how to investigate and solve the problem?

Thanks in advance,
Matt

---

### Post by sudodus on 2013-10-28
Welcome to the Ubuntu Forums :-)

I think there are a few possible causes of the problem.

1. The computer has too little horsepower for the desktop environment. If this is the case, Lubuntu or Xubuntu would do better. An alternative is to install lubuntu-desktop or xubuntu-desktop alternatively 'only' lxde or xfce4 into Ubuntu and select desktop environment at the log in screen (click on the round symbol near the window where to enter the password).

2. The graphics driver is not working well with the graphics chip/card. If this is the case you could try some other proprietary driver.

3. VLC is not working well in your computer (although it is good in many cases). You can try another light-weight video player, for example ***mplayer2***.

If you post the specs of your computer, it will be easier to give relevant advice.

- Brand name and model
- CPU, RAM (size), graphics chip/card

---

### Post by elo96 on 2013-11-17
Hi sudodus,

My apologies for not replying: I thought I'd get an email when someone responded so hadn't checked the thread. I've found that I had issues with DVDs on the windows partition too, so think it may actually be a hardware issue since, as I understand it, the system settings for the two partitions are distinct?

Thanks again,
Matt

---

### Post by sudodus on 2013-11-17
I'm not sure what you mean. The system settings or Ubuntu and Windows are independent of each other. So if you have similar problems it might be that the hardware is setting the limit.

If you post the specs of your computer, it will be easier to give relevant advice.

---

### Post by elo96 on 2013-11-18
> **sudodus said:**
> I'm not sure what you mean. The system settings or Ubuntu and Windows are independent of each other. So if you have similar problems it might be that the hardware is setting the limit.

If you post the specs of your computer, it will be easier to give relevant advice.

The graphics card is a Radeon HD 2400 PRO/XT and I have 4GB of RAM. What other information would be useful?

---

### Post by sudodus on 2013-11-19
Also the CPU specification would be very useful, and if possible also the computer brand name and model.

Unfortunately many Radeon cards have poor drivers for linux. I don't know your particular card, so I cannot recommend either the built in driver or a proprietary one, but I know many other people use Radeon cards with linux. [COLOR=#ff0000]I hope someone with experience of your [/COLOR][COLOR=#ff0000]Radeon HD 2400 PRO/XTcard will chip in and give advice.[/COLOR]

---

### Post by elo96 on 2013-11-19
The output of "cat /proc/cpuinfo" is
```

processor         :0
vendor_id        :GenuineIntel
cpu family       :6
model              :15
model name     :Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping           :11
microcode       :0xb3
cpu MHz                     :1998.000
cache size        :4096 KB
physical id       :0
siblings            :2
core id             :0
cpu cores         :2
apicid              :0
initial apicid    : 0
fdiv_bug         :no
hlt_bug                        :no
f00f_bug         :no
coma_bug        :no
fpu                   :yes
fpu_exception : yes
cpuid level       :10
wp                   :yes
flags                :fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflushdts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebsbts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcmlahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips         :4621.21
clflush size      :64
cache_alignment         : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
 
processor         :1
vendor_id        :GenuineIntel
cpu family       :6
model              :15
model name     :Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping           :11
microcode       :0xb3
cpu MHz                     :1998.000
cache size        :4096 KB
physical id       :0
siblings            :2
core id             :1
cpu cores         :2
apicid              :1
initial apicid    : 1
fdiv_bug         :no
hlt_bug                        :no
f00f_bug         :no
coma_bug        :no
fpu                   :yes
fpu_exception : yes
cpuid level       :10
wp                   :yes
flags                :fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflushdts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebsbts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcmlahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips         :4621.21
clflush size      :64
cache_alignment         : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```
It's a Mesh machine, but not sure about the model I'm afraid!

---

### Post by sudodus on 2013-11-19
I think ***your computer should be able to play DVD video without any problems***, but it might have problems with HD video, depending on the cooperation between the video card and its driver. If you have similar problems with both Windows and Ubuntu playing DVD video, there might be some other problem, a hardware problem.

[COLOR=#ff0000]I hope someone with experience of your [/COLOR][COLOR=#ff0000]Radeon HD 2400 PRO/XTcard will chip in and give advice.[/COLOR]

---

