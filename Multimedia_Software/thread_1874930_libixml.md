---
title: "libixml"
date: 2011-11-04
forum: Multimedia Software
---

### Post by alchemist.vk on 2011-11-04
Hi all,
I am trying to install ushare  , but while running command ./configure , getting error like 'unable to locate package libixml'. 
The same error is reported in other post and suggested way was entering this command 'sudo apt-get install libupnp-dev', but this again popping up error like 'unable to locate package libupnp-dev'. 

 Please let me know how to overcome this one.
Thanks in advance.

---

### Post by ninhalo5 on 2011-11-12
Try this:
```
sudo apt-get install build-essential manpages-dev autoconf automake libupnp-dev libupnp3-dev
``` the libixml is in there.

---

