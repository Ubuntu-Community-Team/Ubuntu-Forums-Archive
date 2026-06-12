---
title: "udev using 100% of CPU and numerous udevd present"
date: 2010-05-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-05-23
I've just noticed that udevd is using 100% of CPU. Of course, I've stopped it (service udev stop) but I suspect it will get up on first reboot... I recall vaguely that we had similar problem before...
Update: It seems it did not start on reboot. It did on previous one. I'll monitor this. I do not know what could have triggered this...

---

### Post by glaze on 2010-05-24
If you run "udevadm monitor", you can see what's causing it.

---

### Post by zika on 2010-05-24
> **glaze said:**
> If you run "udevadm monitor", you can see what's causing it.Thank You, I'll use it next time it goes crazy... :)
Update1: I've got some spare minutes and I tried. It seems that this happens with 2.6.34-999 (current). I'll investigate a bit more. No, udevadm did not give me any useful info. I'm not sure if previously this happened with 2.6.34-999 or 2.6.34-3-preempt...
Update2: Yes, the problem is with 2.6.34-999 (23.05.2010.) Sorry for the false alarm.

---

### Post by zika on 2010-05-27
It happens only with 2.6.34-daily... At the start I have a zillion of udevd's... If I do *sudo killall udevd*, everything settles and the rest of session is OK. Anyone else with the same "problem"...?

---

### Post by andrewthomas on 2010-05-27
Yeah, I have a bug in at kernel.org

[https://bugzilla.kernel.org/show_bug.cgi?id=16052](https://bugzilla.kernel.org/show_bug.cgi?id=16052)

I began to get it when I applied the -git9 patch to the 2.6.34 source.

---

### Post by andrewthomas on 2010-05-31
this problem has been fixed for me with both 2.6.34-git16 (20100530) & 2.6.35-rc1

---

