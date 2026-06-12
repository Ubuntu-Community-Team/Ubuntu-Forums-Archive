---
title: "Auto-load Driver Module"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by tatemononai on 2009-01-12
Ok, I just went through one heck of an ordeal to get my wireless adapter working with Ubuntu 8.1.  I'm a very experienced Windows software engineer, but this is my first time venturing into the world of Linux.  I had to freaking compile a driver just to get my wireless working... boo!  

Anyway, it's working now but I have to reinstall the driver module every single time I boot, which is a huge hassle.

I've added the module to etc/modules but it still doesn't load automatically.  When I run "modprobe" it cannot find the module either, which is probably the issue I'm sure.  I have to rerun "insmod" everytime I boot up.

How do I get my .ko file permanently installed so it can auto-load?  

I copied the .ko file to /lib/modules/2.6.27-9-generic/kernel/drivers

Thanks.

---

### Post by Ayuthia on 2009-01-12
> **tatemononai said:**
> Ok, I just went through one heck of an ordeal to get my wireless adapter working with Ubuntu 8.1.  I'm a very experienced Windows software engineer, but this is my first time venturing into the world of Linux.  I had to freaking compile a driver just to get my wireless working... boo!  

Anyway, it's working now but I have to reinstall the driver module every single time I boot, which is a huge hassle.

I've added the module to etc/modules but it still doesn't load automatically.  When I run "modprobe" it cannot find the module either, which is probably the issue I'm sure.  I have to rerun "insmod" everytime I boot up.

How do I get my .ko file permanently installed so it can auto-load?  

I copied the .ko file to /lib/modules/2.6.27-9-generic/kernel/drivers

Thanks.

Have you run:
```
sudo depmod -a
```It builds the dependencies for the modules in /lib/modules and hopefully that will fix your problem.

---

