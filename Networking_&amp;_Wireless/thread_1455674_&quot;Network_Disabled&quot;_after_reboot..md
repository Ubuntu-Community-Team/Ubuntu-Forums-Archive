---
title: "&quot;Network Disabled&quot; after reboot."
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by monofonik on 2010-04-16
I'm running 10.04 beta2. I installed a bunch of updates last night, rebooted, and networking was disabled. I tried running /etc/init.d/network restart or whatever, to no avail.

anyone got any ideas? I think I might have to reinstall..

---

### Post by idef1x on 2010-04-16
If it happened after a hibernate or suspend : check the following bug report and solution :

[http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html)

It worked for me!

---

### Post by monofonik on 2010-04-16
Yeah dude! I just remembered it happened after my battery died.

I'm in Windows right now, so I'll copy/paste those to a text file and open it from my ubuntu environment.

hopefully in like five minutes I'll be posting from Ubuntu, praising you for your awesomeness!!

---

### Post by monofonik on 2010-04-16
YEAH!!! it worked. thank you so much!

---

### Post by idef1x on 2010-04-16
you're most welcome :) Especially to help someone away from Microsoft ;)

---

### Post by BennieBlount on 2010-04-18
Had the same problem this morning. Shut down beta 10 Ubuntu last night and this morning on boot I got the "Networks Disabled" thing. Thanks for the answer, it worked great. I saved a text file of the fix, just in case it happens again.

Is this a bug that will be fixed in the final release?

Thanks,

Bennie

---

### Post by Arla on 2010-04-18
I'll third this, happened to me first thing this morning, after something went wrong when I tried to suspend my laptop last night (it wouldn't go into suspend, something was stopping it, but not sure what).

---

