---
title: "Network problem in Ubuntu 11.04"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by soumikgh on 2011-08-04
guys pls help me with my problem 
here it goes i hv recently installed ubuntu 11.04 dual boot with windows 7. everything went well except the network. I have a wired internet connection i.e. broadband. my internet works well in windows as well as in ubuntu 10.10 but not in ubuntu 11.04. i have tried the command - 'sudo pppoeconf' - but it doesn't complete . when it loads my the network drivers it stops. it doesn't progress. pls tell me what to do? im in desperate need for help.
thank you

---

### Post by lkjoel on 2011-08-04
Could you give me the output of these Terminal commands?
```
ifconfig
iwconfig
nm-tool
lsb_release -a
uname -a
lspci -vv

```

---

