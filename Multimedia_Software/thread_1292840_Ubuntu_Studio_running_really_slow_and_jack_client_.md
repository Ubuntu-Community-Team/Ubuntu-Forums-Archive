---
title: "Ubuntu Studio running really slow and jack_client_thread zombified"
date: 2009-10-16
forum: Multimedia Software
---

### Post by davemar on 2009-10-16
I've just installed Ubuntu Studio 9.04 on a 32-bit machine. It's not a particularly fast machine (quite old), but I would expect it to do the basics.

I'm trying to run jack and ambdec with aplay going through it. When I run aplay it clearly tries to use jack, but falls over and spits out this error:
```
jack_client_thread zombified - exiting from JACK
```

Also everything is running morbidly slowly, even with jack disabled things are a bit sluggish, but with jack and qjackctrl running, along with ambdec (it's an ambisonics decoder) it all is on the brink of seizing up. I can't imagine any of these things are particularly intensive processing wise.

Is there something just flawed with the RT kernel, or does it require a far more powerful machine than I'm using?

---

### Post by davemar on 2009-10-16
Just as a check of what processor I'm running I did a 'cat /proc/cpuinfo' and got this (editted):
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 4
cpu MHz		: 375.000
cache size	: 1024 KB
bogomips	: 5985.00

```

Am I really running my 3GHz processor at only 375MHz?! Or is this a false reading?

Just chucked a Knoppix LiveCD into an identical PC in the office to check the same thing and it comes up with the same result.

---

### Post by davemar on 2009-10-19
I googled around a bit and it seems some CPUs drop their speeds when the load is low, so I suspected this is why I'm only getting a reading of 375MHz. So I pushed the load up by running a few things (enough to grind things to a near standstill) and again /proc/cpuinfo only shows 375MHz. So it appears the CPU isn't getting it's speed kicked up again.

---

