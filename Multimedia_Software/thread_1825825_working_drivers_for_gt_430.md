---
title: "working drivers for gt 430 ?"
date: 2011-08-15
forum: Multimedia Software
---

### Post by js_theking on 2011-08-15
I'm looking for a WORKING driver for my Geforce GT 430 1GO DDR3. It seems like every drivers I tried screwed up my computer so I had to format it. 

Is anyone having a working geforce gt 4XX (unity, compiz etc) ? I'm stuck on gnome basic without effects. Thanks.

---

### Post by js_theking on 2011-08-15
So I managed to install NVIDIA accelerated graphics driver, recommended by Jockey. But the driver is installed but not in use by the system.
 So apparently I need this :[B] linux-restricted-modules-2.6.38-10
[/B]
But there's a problem 
```
defenc3@defenc3-homepc:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-2.6.38-10-generic
E: Couldn't find any package by regex 'linux-restricted-modules-2.6.38-10-generic'

```How can I install this package ? I searched with synaptic but never found it.

---

