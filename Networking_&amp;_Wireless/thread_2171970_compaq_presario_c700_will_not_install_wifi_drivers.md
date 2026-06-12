---
title: "compaq presario c700 will not install wifi drivers"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by jason27 on 2013-09-02
It throws up error message WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module

It does that on additional drivers.i need help.Ive seen forms on how to do it but its over my head.First time user here.
Thanks jason

---

### Post by varunendra on 2013-09-03
Hello Jason ! Welcome to the forums !! :)

Please open a terminal (Ctrl+Alt+T) and enter the following command (you may copy-paste to avoid errors) :
```
lspci -nnk | grep -iA2 net
```
Post back its output here so we can see which wireless card it has.

By the way, "nvidia_current" is not a wifi driver, it is a graphics one.

---

