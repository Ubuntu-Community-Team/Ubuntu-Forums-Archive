---
title: "Hard freeze when connecting to secure wireless! (8.10 Intrepid, Lenovo R61, Intel)"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by itsdho on 2009-01-26
I just upgraded to Ubuntu 8.10 Intrepid Ibex (from Hardy Heron). I'm on a Lenovo R61 laptop with an Intel wireless card.

When I connect to a secure wireless network, it works for a short time.
But after about 5 minutes, my CPU usage shoots up to 100%. Soon afterwards, my laptop freezes completely!
I can only hold down the power button to turn it off. :(

(Also, a couple of times when my laptop was frozen, my wireless and caps-lock LEDs were blinking rhythmically. Does this indicate a kernel panic or something?)

If I can quickly run **top** before my laptop locks up, it shows me that the CPU-eating processes are:
```
dd
klogd
syslogd
```

Looking at my logs, **/var/log/syslog**, **/var/log/messages**, and **/var/log/kernlog** are all huge (>300 megabytes each!) and growing rapidly.
There are many many many repeats of the following:

```
Jan 26 14:09:53 rhyme kernel: [ 2750.930565]  =======================
Jan 26 14:09:53 rhyme kernel: [ 2750.932978] bad: scheduling from the idle thread!
Jan 26 14:09:53 rhyme kernel: [ 2750.932982] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
Jan 26 14:09:53 rhyme kernel: [ 2750.932984]  [<c037c4b6>] ? printk+0x1d/0x1f
Jan 26 14:09:53 rhyme kernel: [ 2750.932988]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Jan 26 14:09:53 rhyme kernel: [ 2750.932990]  [<c012107f>] dequeue_task+0xcf/0x130
Jan 26 14:09:53 rhyme kernel: [ 2750.932993]  [<c012112a>] deactivate_task+0x1a/0x30
Jan 26 14:09:53 rhyme kernel: [ 2750.932996]  [<c037cad3>] schedule+0x4b3/0x790
Jan 26 14:09:53 rhyme kernel: [ 2750.932999]  [<c01028cd>] cpu_idle+0xbd/0x140
Jan 26 14:09:53 rhyme kernel: [ 2750.933002]  [<c036ee83>] rest_init+0x53/0x60

```
See the attachment for more details.

**lspci -v** gives me:

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1110
	Flags: fast devsel, IRQ 17
	Memory at df3fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

I have no problems with my wired connection, or with wireless on an unsecured network.
(And I never had problems with any of this when I was using Hardy Heron.)

What's going on? Can someone help me?

Thanks!

---

### Post by lamborghiniwang on 2009-01-27
I am having the same problem on a Thinkpad T61p. It seems whenever I try to switch on/off the wireless for a few times(or just simply suspend/resume for a couple of times), something weird would happen.

---

### Post by itsdho on 2009-01-27
Further investigation reveals [https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless](https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless)

and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

So it looks like:
1) it is indeed a kernel panic, and
2) many other people with Intel wireless are experiencing the same problem.

Installing **linux-backports-modules-intrepid**, as suggested in the release notes, does not fix this problem for me. :(
I'll keep searching for more information.

---

### Post by lamborghiniwang on 2009-01-28
I also found another bug reporting regarding this issue:
[#286285]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285"), and according to this bug report: 
> 
***Important summary for those experiencing this bug***
Kernel versions where this bug is fixed:
1) 2.6.27-10 from intrepid-proposed

Kernel versions where this bug is NOT fixed (if you are running one of these, please upgrade to known working kernel):
1) 2.6.27-7 from intrepid
2) 2.6.27-9 from intrepid-updates and intrepid-security


A side note: I found there is 2.6.27-11 kernel in the Intrepid proposed repo, not sure if it is stable enough though.

---

### Post by itsdho on 2009-01-28
Good call! The bug you found is almost certainly the same one I'm getting.

I think 2.6.27-11 just came out on -updates this morning.
I'm using it right now, and it seems to be working; I haven't had a kernel panic yet. Tentative yay! :D

(Note: I also uninstalled linux-backports-modules-intrepid, as suggested on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285), before applying the update.)

---

