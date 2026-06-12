---
title: "Bridge + eth0 for qemu"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by brazoayeye on 2010-06-25
Hi! 

This is my problem:

1) I need to use qemu in bridged mode, so i need to configure a bridge with my phisical card, eth0. 

First I'll ask you my doubts:

a) when i make a bridge (br0) with ip 192.168.1.200 and a network interfaces (eth0) with ip 192.168.1.2 where is the phisical card?
b) If i ping someone with wich interface i'll do?
c) What do the other interface?

Now here what i did:

```
sudo ifconfig eth0 0.0.0.0
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo ifconfig br0 192.168.1.200
sudo ifconfig br0 up
sudo ifconfig eth0 192.168.1.2
```

ok, all works.


The problem is how to automate the code using interfaces.

I tried with lots of options but no results (many times system can't boot, so i need a live to restore interfaces)

Any ideas?

Thanks

---

