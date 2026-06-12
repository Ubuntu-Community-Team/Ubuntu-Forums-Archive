---
title: "Which Nvidia Driver for Quadro 400 on 12.10?"
date: 2012-12-23
forum: Multimedia Software
---

### Post by kmand on 2012-12-23
I recently upgraded to ubuntu 12.10 on a box with a Nvidia GT216GL [Quadro 400]. Lately my Unity Desktop session has been going crazy from time to time with messed up graphics all over the screen.

I also see quite a few Nouveau messages of all sorts in syslog.

modinfo says I'm running

3.5.0-21-generic SMP 
nVidia Riva/TNT/GeForce
Stephane Marchesin

Am I running the right version?

---

### Post by ranger1021994 on 2012-12-23
> **kmand said:**
> I recently upgraded to ubuntu 12.10 on a box with a Nvidia GT216GL [Quadro 400]. Lately my Unity Desktop session has been going crazy from time to time with messed up graphics all over the screen.

I also see quite a few Nouveau messages of all sorts in syslog.

modinfo says I'm running

3.5.0-21-generic SMP 
nVidia Riva/TNT/GeForce
Stephane Marchesin

Am I running the right version?

Can you please describe what problem are you facing ?

---

### Post by kmand on 2012-12-23
> **ranger1021994 said:**
> Can you please describe what problem are you facing ?

The desktop display gets all scrambled, with pieces in random places. Sometime enough is visible that I can logout and back in, other times have to reboot.

---

### Post by ranger1021994 on 2012-12-23
please try unity --reset

---

### Post by kmand on 2012-12-23
> **ranger1021994 said:**
> please try unity --reset


$ unity --reset
ERROR: the reset option is now deprecated

No luck with that. By the way, the desktop does normally work properly, but it has gone into scrambled mode 3 times in the last 2 days, a couple of times when I wasn't even in front of the display.

--

The reason I suspect the Nvidia Driver is I see messages like

 kernel: [ 8275.060290] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2 Get 0x002002aac4 Put 0x002002b5c0 IbGet 0x00000f5c IbPut 0x00000f5d State 0x80004804 (err: INVALID_CMD) Push 0x00502031

in syslog. Although I don't really know they correspond to the scrambling.

---

### Post by ranger1021994 on 2012-12-24
You had recently edited settings in Compiz ?

---

### Post by kmand on 2012-12-24
> **ranger1021994 said:**
> You had recently edited settings in Compiz ?

No.

---

### Post by kmand on 2013-01-06
I switched to the proprietary Nvidia driver and the problem has gone away.

---

