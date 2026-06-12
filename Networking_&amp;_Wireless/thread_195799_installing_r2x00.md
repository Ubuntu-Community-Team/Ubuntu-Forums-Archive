---
title: "installing r2x00"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by nishoba on 2006-06-13
hello
 
i'm new to linux, so i need a little help installing drivers
i'm trying to install rt2x00-2.0.0-b3 drivers because under dapper the native rt2500-1.1.0 drivers don't work well, sometime they work normal, sometimes they don't see my pcmcia wireless card...(all worked well under ubuntu :(

ok, i make the drivers with make
and then i need tu install them
so the question is, do i:
```
sudo make install
```
or don't?

in the readme file they say:
> When installing the modules with 'make install' the installation routine
 will create a new folder named 'rt2x00' inside the kernel modules directory
 usually /lib/modules/$(uname -r)/, all modules (including the ieee80211 stack
 will be installed into that directory.
 Some distributions however do not comply with the kernel guidelines
 which causes the kernel to install the modules into the wrong directory.
and this is true with ubuntu

so how to install drivers?
how to uninstall rt2500-1.1.0 drivers, if i have to?

a step by step guide would be great :p 
thx

---

