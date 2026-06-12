---
title: "Ubuntu wireless network recognition on a Dell Inspiron 5100"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by Quantum Anomaly on 2009-09-30
I just installed Ubuntu 9.04 on an old Dell Inspiron 5100 and it works great except for one crucial thing: the wireless connectivity.

An attempt to find the answer has led me down a rabbit hole of conflicting advice. What are the steps to follow to get your wireless network to show up in Ubuntu with an Inspiron 5100? I'm sure somebody knows since it's an old machine.

Thanks in advance for any help.

---

### Post by A_Fiachra on 2009-09-30
What do you get when you do:

```


sudo lshw -C network


```

This should tell you what hardware you have for wireless and whether it is enabled.  If you paste the results here people can help.

HTH

---

