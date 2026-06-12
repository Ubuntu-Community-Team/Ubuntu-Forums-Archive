---
title: "Kaffeine crashes my system"
date: 2008-06-04
forum: Multimedia Software
---

### Post by mlilien on 2008-06-04
I recently did a reinstall of Hardy and now whenever I watch a video using Kaffeine, after about 10 minutes of playing fine, my laptop shuts down.  My first install of Hardy didn't have this problem, and I haven't been able to find anything about it anywhere else.

I'm using Ubuntu on a Lenovo t60p with a ati graphics card.

Any clue what could be causing this?

Thanks

---

### Post by xc3RnbFO8P on 2008-06-04
Maybe overheating?
You can check in Synaptic Package Manager, **libsensors**

---

### Post by mlilien on 2008-06-04
What's a normal operating temperature?  I'm usually between 60 and 70 (haven't paid attention while running kaffeine), give or take.  And how would I go about cooling down my system?  I already have the cpu set to run on powersave mode.

Thanks.

---

### Post by mlilien on 2008-06-04
Ok, this seems like it could be the culprit.  after just a couple minutes of playing a video, my cpu temp jumped up to 74 degrees, with kaffeine using 25 to 50% of my cpu.  Any ideas on what I could do?

Thanks

---

### Post by xc3RnbFO8P on 2008-06-04
I found this:

>  iMatt wrote on 2008-03-31: (permalink)

My T60p overheating problem with 7.10 appears to be solved.

I did a BIOS upgrade to version 2.21 from the IBM/Lenovo website. Released 2008/02/13.
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63027](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63027)

The temperature skyrocketed when I ran a cpuburn test (up past 80C for 20 mins) but it wouldn't lock up. Minutes prior to the update, the machine would lock up in the 60-65C range.

It also appears the fan is running about 600rpm faster by default. Verified by "cat /proc/acpi/ibm/fan". I no longer have to physically set the fan to speed "7" anymore.

This leads me to believe it wasn't solely a CPU temperature issue, as the machine can run MUCH warmer now without lockup.
To all out there experiencing this issue, check for a BIOS upgrade - it just may fix the problem.

Should the problem reoccur I will post up.  

Did you update?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213818]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213818")

---

### Post by mlilien on 2008-06-05
Thanks, updating the bios seemed to work.  I also set my gpu to level 1 which seemed to help a bit.  However, according to conky, my cpu is still hanging around 60-65 when I'm just doing normal internet browsing and whatnot, which seems a bit high.

---

