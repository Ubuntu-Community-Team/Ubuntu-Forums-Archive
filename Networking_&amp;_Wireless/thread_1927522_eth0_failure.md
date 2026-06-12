---
title: "eth0 failure"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by pmac95 on 2012-02-18
Hello, I was following a tutorial on iptables and tinkled a bit. Now I cant get up eth0.
this is the error message when I try to network restart from the command line: 
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

 this is my /network/interfaces file
```
auto lo
iface lo inet loopback

#primary interface
auto eth0
iface eth0 inet dhcp
```
 I am fairly new to networking.
Thank you for reading

---

### Post by praseodym on 2012-02-18
Hi,

how do you want to connect? Router/Modem or single modem? Please show the outputs of

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```
Remove the iptables according to this:
```
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by pmac95 on 2012-02-19
Thanks a lot praseodym, removing the iptables seems to have done the job.  I appreciate your help, thanks

---

