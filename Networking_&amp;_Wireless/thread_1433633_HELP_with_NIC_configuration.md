---
title: "HELP with NIC configuration"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by twister89 on 2010-03-19
Hello guys

I've just configured an ubuntu server VM in virtualbox but i've some problem with the NICs.

The current configuration is of one NIC connected to the host only lan and one to the Internet NAT, connection which is, furthermore, behind an http proxy.

My problem is that if the eth0, connected to the Host Only, is up internet have big problems or doesn't  work at all. I think the problem is something around the routing matter: i should say that packets pointing to internet should go trough the eth1 NIC (the NAT-ed one) and the others, pointing the lan (192.168.56.*), should be sent to the eth0.

So how could I do?? Could you help me??

---

### Post by suseendran.rengabashyam on 2010-03-19
Hi,

Can you post the output of the following command

```
sudo route -n
```

---

