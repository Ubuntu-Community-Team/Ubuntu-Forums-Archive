---
title: "Ubuntu - Realtek Networking issues"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by rohitsivakumar on 2009-07-02
Is there a network problem in Ubuntu version 8.04 version or 9.04 version  like dropping of network packets (over a wired ethernet connection) or are there any issues with reference to network card drivers of Realtek?
 
We have not been able to get the Ubuntu 8.04 version working with a realtek network card and we are also facing huge network packet dropping kind of problems. The same LAN environment however works fine when connected with the windows pc. 
 
What could be the problem.

---

### Post by alphacrucis2 on 2009-07-02
> **rohitsivakumar said:**
> Is there a network problem in Ubuntu version 8.04 version or 9.04 version  like dropping of network packets (over a wired ethernet connection) or are there any issues with reference to network card drivers of Realtek?
 
We have not been able to get the Ubuntu 8.04 version working with a realtek network card and we are also facing huge network packet dropping kind of problems. The same LAN environment however works fine when connected with the windows pc. 
 
What could be the problem.


If it isn't working then probably a driver issue. What do you get from

```
sudo lshw -C network
```

---

### Post by superprash2003 on 2009-07-02
dorpping of network packets could be due to low MTU values , check your mTU values , post output of ifconfig from the terminal

---

