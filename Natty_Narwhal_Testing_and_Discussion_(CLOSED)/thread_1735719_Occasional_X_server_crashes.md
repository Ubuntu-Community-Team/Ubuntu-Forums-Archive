---
title: "Occasional X server crashes?"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Shmantiv_Radio on 2011-04-21
I've had 2 and been sent back to the login screen.

Is anyone else experiencing this?

---

### Post by cariboo on 2011-04-21
I haven't seen any X crashes running nvidia-current

---

### Post by Shmantiv_Radio on 2011-04-21
> **cariboo907 said:**
> I haven't seen any X crashes running nvidia-current

I'm using the default Intel driver =/

---

### Post by cariboo on 2011-04-21
My netbook uses the Intel i915 driver, I haven't had any X crashes with it either.

---

### Post by akvik on 2011-04-26
I installed natty yesterday, and today X crash just about every 5-10 minutes, sending me back to the login screen. Yesterday all worked fine for hours. There was no X update this morning either.

Will check more details in the logs.

Intel chip, HP 2640 laptop, latest natty, using external screen.

---

### Post by akvik on 2011-04-26
I checked my logs and cpufreqd created a lot of fuss about not being able to set the "Performance high" profile.

I uninstalled cpufreqd and X haven't crashed since then. Might be a stroke of good luck though. I don't consider my problem solved yet, but it's promising.

Did my natty upgrade as a straight-up upgrade from Maverick, without uninstalling any packages from third-party or multiverse. So far this has been the only problem, and I had a lot of third-party applications.

---

### Post by areteichi on 2011-04-26
Yeah this happens to me too. I use Intel 945GM chipset. It happens to me approximately once a day or every other day.

---

### Post by akvik on 2011-04-26
Have now run Natty the whole day on max, plenty of apps running constantly. All problems with X crashing from this morning are gone after I uninstalled cpufreqd. Before that X crashed every 5-10 minutes, sending me back to the login screen.

I consider my problem solved, even if it probably isn't the solution to Shmantiv_Radio's problem - or do have cpufreqd installed? If so try uninstalling it.

---

### Post by areteichi on 2011-04-28
Mine just crashed again, on the day Natty is supposed to be released. Nothing catastrophic but I hope my problem will go away soon too.

---

### Post by Augusto_R on 2011-04-28
My X crashes every few days too. Any Bugs to subscribe to? Happy to try to provide some error logs. For the moment this is what my X.org.log has to say. This time happened very early on while I browsed a website on firefox

> Backtrace:
[   210.241] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[   210.241] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[   210.241] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xff540c]
[   210.241] 3: /usr/bin/X (_CallCallbacks+0x3e) [0x8074e1e]
[   210.241] 4: /usr/bin/X (WriteToClient+0x267) [0x80a7607]
[   210.241] 5: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x62) [0x2debf2]
[   210.241] 6: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x75) [0x2dcfc5]
[   210.241] 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0x642000+0x2261c) [0x66461c]
[   210.241] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x642000+0x87c2) [0x64a7c2]
[   210.241] 9: /lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xf5) [0xdc4665]
[   210.241] 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0x642000+0x7927) [0x649927]
[   210.241] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[   210.242] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1f3a]
[   210.242] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[   210.242] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[   210.242] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x126e37]
[   210.242] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[   210.242] Segmentation fault at address 0xb52f7008
[   210.242] 
Caught signal 11 (Segmentation fault). Server aborting
[   210.242] 


---

