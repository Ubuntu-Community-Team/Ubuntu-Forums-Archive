---
title: "Help! Unity crash"
date: 2013-06-17
forum: Multimedia Software
---

### Post by nibal on 2013-06-17
Hi,

I just installed unity and ubuntu-desktop in my xubuntu 12.10 desktop. I then proceeded to configure compiz. Enabled cubes (disabled wall) and compiz crashed hard. It took unity with it, so I now have no Desktop menu or unity bar and pretty much my desktop is useless! Thank God I can still shutdown from an xterm ;)

I have disabled the cube since then, but unity and Desktop Menu are still MIA. Each time I reboot I get an annoying warning "Application crash". :(Anyone knows how to get them back?

Thanks,
Nikos

---

### Post by ajgreeny on 2013-06-17
Try ```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```
That used to reset compiz and unity to the defaults in a previous ubuntu version, but I'm not sure if it works now; things may have changed.

---

