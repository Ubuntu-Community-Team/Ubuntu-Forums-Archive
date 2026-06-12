---
title: "Ubuntu does not get internet connection"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by surenot on 2013-02-14
I have the Ubuntu base system installed on a iBook G3 computer (no gui), and it will not connect to the internet.  It seems to be able to identify the network interfaces, but every time I run a command like apt-get or ping it returns errors.  The internet connection is wired, so I don't think it's an issue with it not being able to get a signal (and other computers are able to connect to the internet using that ethernet wire also).

I'm not sure if this is related to the problem at hand, but during installation I used the expert mode, and choose the linux-generic-3.XXXX-ppc-smp kernel.  Should I have used a different kernel?  It also get the error 'mountall failed' every time it boots up, could this also have something to do with the problem?

---

### Post by praseodym on 2013-02-15
Hi,

please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

