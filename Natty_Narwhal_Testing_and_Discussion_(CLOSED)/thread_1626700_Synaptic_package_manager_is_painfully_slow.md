---
title: "Synaptic package manager is painfully slow"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-11-20
Is it just me, or has the Synaptic interface become sluggish and unresponsive to click or keyboard presses?

---

### Post by Vanishing on 2010-11-20
> **Starks said:**
> Is it just me, or has the Synaptic interface become sluggish and unresponsive to click or keyboard presses?

I was just about to open a post like this.:p

---

### Post by MacUntu on 2010-11-20
It's because of this messed-up apt-xapian-index thingy that also slows down software-center.

---

### Post by arpanaut on 2010-11-20
Yup, driving me bonkers too.

---

### Post by Harry33 on 2010-11-20
> **Starks said:**
> Is it just me, or has the Synaptic interface become sluggish and unresponsive to click or keyboard presses?

I have filed a bug report on this issue:
bug #675641

This is about the apt packages and enabled compressed indexes.

Downgrading to the version 0.8.8ubuntu2 will solve this.

---

### Post by Anduu on 2010-11-20
This has been a nightmare for me the last few days.

I am having dependency issues getting Gnome Shell to compile and trying to do searches in Synaptic is nigh on impossible :/

---

### Post by MacUntu on 2010-11-20
Ah, *that's* why ppa-purge fails. Opened a [bug report](https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/677961).

---

### Post by Anduu on 2010-11-20
> **MacUntu said:**
> Ah, *that's* why ppa-purge fails. Opened a [bug report](https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/677961).

Yep...that's why I was forced to manually fix stuff in Synaptic...sigh.

---

### Post by autocrosser on 2010-11-21
Did a "affects me" on both reports....

---

### Post by efflandt on 2010-11-26
I just got into natty with the Nov 23 iso, and if I refresh Synaptic it never finishes Reindexing for Quick search, and has some processes that appear to each be using 100% of cpu time in top that never finish, although, it is strange that top shows total cpus at 0.3%:

```
top - 22:35:05 up 20 min,  3 users,  load average: 2.78, 2.79, 1.84
Tasks: 160 total,   4 running, 156 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us, 17.4%sy, 49.8%ni, 32.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8121640k total,  1323308k used,  6798332k free,    60544k buffers
Swap:        0k total,        0k used,        0k free,   408236k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1684 root      30  10  322m 145m  11m R  100  1.8  11:55.05 update-apt-xapi
 1706 root      30  10  322m 144m  11m R  100  1.8  10:49.56 update-apt-xapi
  904 root      20   0     0    0    0 R   74  0.0  15:40.64 kworker/0:2
 1148 root      20   0  139m  37m  18m S    1  0.5   0:14.25 Xorg
 1446 efflandt  20   0  242m  35m  23m S    0  0.4   0:03.76 compiz
 1725 efflandt  20   0  256m  16m  11m S    0  0.2   0:00.50 gnome-terminal
 1748 efflandt  20   0 19276 1328  952 R    0  0.0   0:00.33 top
    1 root      20   0 23848 1992 1296 S    0  0.0   0:00.97 init

efflandt@natty-usb:~$ grep MHz /proc/cpuinfo
cpu MHz        : 2667.000
cpu MHz        : 3201.000
cpu MHz        : 3201.000
cpu MHz        : 3201.000
efflandt@natty-usb:~$ grep MHz /proc/cpuinfo
cpu MHz        : 2667.000
cpu MHz        : 3201.000
cpu MHz        : 1200.000
cpu MHz        : 3201.000
```And what is kworker?  That one shows a constant 74% or more cpu time even when not doing anything.

This is a regular install, because iso will not run live with nouveau (no GL), and nvidia cannot be installed on usb iso even with persistent data.  i5 650 3.2 GHz, 8 GB, nvidia GT 430

---

### Post by Harry33 on 2010-11-26
There is a fix in Natty repos now:
apt packages v. 0.8.9ubuntu4.

The compressed indexes have been temporarily turned off now.

And synaptic is fast again.

See the bug #675641

---

### Post by frozenjim on 2010-12-13
I had the same problem; Synaptec became 100% unusable for minutes at a time whenever I did almost anything.  ie. select a package and sit for three minutes waiting while the Synaptec screen went dark.

There is a fix somewhere - I'm trying to locate it now - that worked for me.  It was as simple as deleting a file.  Did that, restarted Synaptec and it blistered along just fine.

So now I'm on another PC with the same problem and I just cannot find that link.  I'll check back if I do find it.

---

### Post by Harry33 on 2010-12-13
> **frozenjim said:**
> I had the same problem; Synaptec became 100% unusable for minutes at a time whenever I did almost anything.  ie. select a package and sit for three minutes waiting while the Synaptec screen went dark.

There is a fix somewhere - I'm trying to locate it now - that worked for me.  It was as simple as deleting a file.  Did that, restarted Synaptec and it blistered along just fine.

So now I'm on another PC with the same problem and I just cannot find that link.  I'll check back if I do find it.

This was fixed about three weeks ago:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641)
It has been applied from apt version 0.8.9ubuntu4.

Do you still have this issue?

---

### Post by dino99 on 2010-12-13
Some patience needed :( , devs are moving from glade to gtkbuilder

---

### Post by Harry33 on 2010-12-13
> **dino99 said:**
> Some patience needed :( , devs are moving from glade to gtkbuilder

What update exactly is causing trouble in Synaptic just now?
I have the most recent updates installed and no problems in Synaptic nor any slowdown effects anywhere.
I am using synaptic_0.75~pre3 (64 bit- Natty).

---

### Post by Harry33 on 2010-12-13
The transition from glade to gtkbuilder concerns especially gnome-power-manager and perhaps checkbox-gtk and libpanel-applet2.0.

---

### Post by frozenjim on 2010-12-14
> **Harry33 said:**
> This was fixed about three weeks ago:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641)
It has been applied from apt version 0.8.9ubuntu4.

Do you still have this issue?

Yep.  I still have the issue.  My apt is 0.7.25.3.ubuntu9.3 which is the latest in the main repository.  I'm guessing you have experimental turned on?

The fix was simple - I just deleted two files from somewhere and it was fixed instantly.  I just cannot recall which two files they were.

---

### Post by Harry33 on 2010-12-14
> **frozenjim said:**
> Yep.  I still have the issue.  My apt is 0.7.25.3.ubuntu9.3 which is the latest in the main repository.  I'm guessing you have experimental turned on?

What the ....?
Oh yes, you do not run Natty, you have Lucid.
This bug (675641) was about Natty.

---

### Post by cariboo on 2010-12-14
> **frozenjim said:**
> Yep.  I still have the issue.  My apt is 0.7.25.3.ubuntu9.3 which is the latest in the main repository.  I'm guessing you have experimental turned on?

The fix was simple - I just deleted two files from somewhere and it was fixed instantly.  I just cannot recall which two files they were.

This is the Natty Testing and Discussion sub-forum, we're all running alpha software.

---

### Post by tonyschmidt on 2010-12-14
good luck

---

### Post by brandon.payton on 2011-01-04
**UPDATE: **I found this issue via search and didn't realize that it was Natty-related. The issue I experienced was with 10.10.

> **Starks said:**
> Is it just me, or has the Synaptic interface become sluggish and unresponsive to click or keyboard presses?
I had the same issue, usually involving quick search or mark/unmark packages. Someone suggested doing a purge/reinstall, but simply deleting /root/.synaptic improved response time for me.

It seemed like an indexing issue, but I didn't see anything in the .synaptic dir that obviously corresponded.

---

