---
title: "Trying to rename eth3 as eth0"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by elperrillo on 2009-08-05
I am having a real problem.

I cloned a ubuntu machine with diferent hardware (and diferent network cards) onto another machine. The problem is that I have DRBL and CLonezilla and a whole bunch of settings that work with the Network Cards named as Eth0 and Eth1, however the new coned machine is detecting the new cards as Eth2 and Eth3, I have tried renaming them and that does not work, as soon as I reboot Ubuntu gets all confused. Can anybody help me? I have 60 computers to clone by tomorrow :(

I would really appreciate it.

---

### Post by t0mppa on 2009-08-05
Not sure what exactly you did to rename the interface, but if you didn't edit the */etc/udev/rules.d/70-persistent-net.rules* file yet, that's where you should look.

---

### Post by elperrillo on 2009-08-05
Awesome, that did it. Thank you so much!

---

