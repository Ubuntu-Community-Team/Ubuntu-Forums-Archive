---
title: "Realtek 8139 problems"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by jason50146 on 2010-08-19
My new ethernet card is a Realtek RTL-8139.  This thing has some problems with Lucid, but I found part of a solution [here]("http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10"), as is shown below.

The problem with this fix is that it does not survive a reboot.  Any ideas on how to make the fix permanent?  

Thanks!


```
1	root@ubuntu:~$ mii-tool eth0 -F 10baseT-FD
2	root@ubuntu:~$ rmmod 8139too
3	root@ubuntu:~$ modprobe 8139too
```

---

### Post by binaryslacker on 2010-12-23
go into your /etc/rc.local and add 

mii-tool eth0 -F 10baseT-FD
rmmod 8139too
modprobe 8139too

all above the exit 0 at the bottom of /etc/rc.local

It should execute those commands whenever you power on your computer.

---

