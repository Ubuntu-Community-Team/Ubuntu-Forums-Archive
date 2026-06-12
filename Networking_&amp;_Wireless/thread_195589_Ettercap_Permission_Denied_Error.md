---
title: "Ettercap Permission Denied Error"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by snakeyes37 on 2006-06-13
Hello,


After using Ettercap then closing it out I keep receiving this error in the terminal window, 


```

root@Nick:~# ettercap -G

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.3: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

```


I already have the latest version of iptables according to synaptic. Perhaps I have my permission set incorrectly? I logged into the root account through the graphical login interface.


Thanks.

---

### Post by snakeyes37 on 2006-06-14
So, does anybody know what this is happening?


Thanks.

---

### Post by Slim Odds on 2006-06-14
Try this:
```
sudo ettercap -G
```

---

### Post by snakeyes37 on 2006-06-15
I've tried that command, its doesn't seem to work. Whats odd is that I'm also receiving this permission denied error on other distros aswell too.

---

