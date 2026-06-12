---
title: "Can connect to network only with live CD - need to troubleshoot"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by AussieGuy on 2013-02-10
I've come into work to find that there was a power outage over the weekend, and and now for some reason my desktop computer running Ubuntu 12.04 (edubuntu) is unable to connect to the University network. 

As an experiment, I rebooted my machine with an Ubuntu 12.04 live CD, and and the network connected immediately, as it should. 

I unplugged the network cable, rebooted into desktop Ubuntu, then plugged the cable back in and rebooted again. Nothing. There would appear to be some setting, somewhere, which is preventing my system from connecting to the network. 

How do I find out what's going on? This is very frustrating, as well as meaning I can't get much work done. 

Thanks very much, 
Al

Thanks

---

### Post by AussieGuy on 2013-02-10
SOLVED IT!

After losing what little hair I have left, I simply removed the kernel module e1000e with rmmod, and then reinserted it with modprobe.

And viola!  I have internet once more.

-Al

---

### Post by wildmanne39 on 2013-02-11
Great! Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

