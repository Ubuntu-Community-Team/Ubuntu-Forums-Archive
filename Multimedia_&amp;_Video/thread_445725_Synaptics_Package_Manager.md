---
title: "Synaptics Package Manager"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by wow20 on 2007-05-16
Hi 

Im very new to Ubuntu operating system so pls help me..

I was trying to install the looking glass 3d effect for my desktop but its failed and when i tried to install any new applications or use the synaptic package manager i couldnt access it.
This occured:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i tried using the terminal but it said that "dpkg" was accessible to only superusers.
pls help...

---

### Post by heimo on 2007-05-16
It may not be enough, but this is where I'd start:
```
sudo dpkg --configure -a
sudo apt-get update

```

I remember a thread on these forums with very similar problem.

---

