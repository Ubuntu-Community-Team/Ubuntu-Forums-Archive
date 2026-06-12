---
title: "Help Compiling New Carl9170 Drivers from Wireless-Testing"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by SleepWalkerX on 2012-05-20
I have custom compiled modules in a while so I forget how its done.

I'm trying to compile the latest carl9170 driver from the wireless-testing.git because my current one is very flakey.

So far I've downloaded the code through git (git clone git://git.kernel.org/pub/scm/linux/kernel/git/linville/wireless-testing.git).  

Then I ran 'make menuconfig' and made sure AR9170 N support was enabled as a module.  I didn't uncheck any other ones.

But here's where I'm stuck.  I'm running the 3.2.0-24-generic kernel for Ubuntu 12.04 x86_64.  The wireless-testing drivers are built for 3.4-rc5 it appears.

Running git tag the following few selections appear:

```
v3.1-rc8
v3.1-rc9
v3.2
v3.2-rc1
v3.2-rc2
v3.2-rc3
```

Would it work if I 'checked out' v3.2 and then compiled as modules?  Or is it slightly off considering the actual kernel is 3.2.0-24-generic?

---

