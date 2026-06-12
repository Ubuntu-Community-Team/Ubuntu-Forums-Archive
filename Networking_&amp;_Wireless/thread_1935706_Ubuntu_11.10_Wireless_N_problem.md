---
title: "Ubuntu 11.10 Wireless N problem"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by A3rios on 2012-03-04
So I just installed ubuntu 11.10 on my computer and found that my wireless speeds dropped to record lows. So i did some research and came across this solution:
```
**sudo rmmod -f iwlagn** **sudo modprobe iwlagn 11n_disable=1**
```Which worked and i tried to make it permanent by using this:

```
[B]gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf
[/B]
```but it dint work and i have to retype the commands in every time i restart. Is there another way i could make this change permanent?

---

### Post by DrPotoroo on 2012-03-05
You are on the right track, but when you edited /etc/modprobe.d/iwlagn-disable11n.conf what did you put in the conf file? It has been ages since I've had to mess with modprobe. Maybe it would just need something like the following line saved in the iwlagn-disable11n.conf file:
```
options iwlagn 11n_disable=1
```

---

