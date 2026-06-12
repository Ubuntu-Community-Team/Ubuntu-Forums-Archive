---
title: "While playing video within firefox - CPU goes high, then shuts down the machine"
date: 2010-09-06
forum: Multimedia Software
---

### Post by sprilutsky on 2010-09-06
Hi there,

Many times, playing video within Firefox drives CPU way high, then reaches 100% and shuts down my machine.

Also noticed that npviewer.bin goes high as well, both take all my CPU 

I have Dual core 3.4 GHz Pentium CPU, running UBUNTU 9.04

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.19

Anyone experienced the same and/or have any advice? Help much appreciated.

Thanks

---

### Post by Yellow Pasque on 2010-09-06
The CPU is overheating..

---

### Post by lovinglinux on 2010-09-06
See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by Yellow Pasque on 2010-09-06
> **lovinglinux said:**
> See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
That might help, but there's a hardware issue here too (overheating under extended load). No system should overheat even when stressed for an extended period of time, especially a desktop. The cooling system probably needs maintainence such as removing dust from the heatsink and maybe redoing the thermal grease. If that doesn't suffice, a better cooler and/or more airflow is needed. If the CPU is a Presler core Pentium D 945/950 (or OC'd equivalent), then a CPU cooler upgrade might be unavoidable if you want to continue stressing the CPU for extended periods of time.

---

### Post by lovinglinux on 2010-09-06
> **Temüjin said:**
> That might help, but there's a hardware issue here too (overheating under extended load). No system should overheat even when stressed for an extended period of time, especially a desktop. The cooling system probably needs maintainence such as removing dust from the heatsink and maybe redoing the thermal grease. If that doesn't suffice, a better cooler and/or more airflow is needed. If the CPU is a Presler core Pentium D 945/950 (or OC'd equivalent), then a CPU cooler upgrade might be unavoidable if you want to continue stressing the CPU for extended periods of time.

Cleaning CPU  fans is the first item on the list :)

---

### Post by Linuxforall on 2010-09-07
Turn off compiz and see if the temps drop.

---

### Post by sprilutsky on 2010-09-07
Thanks for your reply. I agree, it vould be overheating, but ... why only from firefox? Playing video from the internal disk or external DVD media does not take cpu high, only maybe 12-15%?

Only Firefox does that. Any other thoughts?

Thanks

---

### Post by Yellow Pasque on 2010-09-07
..because Flash on Linux is extremely inefficient (even worse than Windoze) and not accelerated by GPU, so it uses lots of CPU. That doesn't change the fact that your CPU cooling setup is inadequate.

---

### Post by lovinglinux on 2010-09-07
> **sprilutsky said:**
> Thanks for your reply. I agree, it vould be overheating, but ... why only from firefox? Playing video from the internal disk or external DVD media does not take cpu high, only maybe 12-15%?

Only Firefox does that. Any other thoughts?

Thanks

Is not Firefox fault and playing videos locally doesn't require the flash plugin, which is the source of the problem. Flash uses too much CPU because it can't use xv output like other players. That's why your CPU usage is low when playing videos locally.

Your problem is most likely to be CPU overheat caused by flash.

I have experienced the same problem on a single core P4 processor. The problem was fixed since I upgrade to a Core2 Duo, which is more powerful and runs with lower temperatures. But the Pentium would overheat after a while, then CPU would spike to 100% and degrade flash video performance.

So, you should make sure your CPU doesn't overheat.

---

