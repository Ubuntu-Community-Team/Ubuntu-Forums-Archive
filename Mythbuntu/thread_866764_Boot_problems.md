---
title: "Boot problems"
date: 2008-07-22
forum: Mythbuntu
---

### Post by Hellfire29 on 2008-07-22
I just built an htpc and when it boots, it displays the login information. Once I enter this, however, it stats "Bash: /dev/null permission denied".
It then waits for an instruction on the command line.
What do I do to remedy this problem, or more specifically, where is whatever I have to start at start up.
My system specs: 
AMD LE-1150 Processor.
Asus m2a-vm motherboard.
Kingston 1gb 667mhz RAM.
Leadtek dtv1800 h Tuner Card.

---

### Post by mrand on 2008-07-22
> **Hellfire29 said:**
> I just built an htpc and when it boots, it displays the login information. Once I enter this, however, it stats "Bash: /dev/null permission denied".
It then waits for an instruction on the command line.
What do I do to remedy this problem, or more specifically, where is whatever I have to start at start up.
My system specs: 
AMD LE-1150 Processor.
Asus m2a-vm motherboard.
Kingston 1gb 667mhz RAM.
Leadtek dtv1800 h Tuner Card.

Searching on "Bash: /dev/null permission denied" in Google turns up a number of bug reports.  Seems the most common cause is the system trying to start start udev when it is already running (possibly because of multiple entries in the rules files under /etc/rc*.d)

This doesn't seem like a Mythbuntu problem though - if the above doesn't help, you'd likely get better help in one of the more general Ubuntu forum(s).


Good luck,

   Marc

---

