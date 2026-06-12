---
title: "Ubuntu will not send Router solicitation"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by psankovic on 2012-11-20
Hello,

Anyone knows how to force ubuntu to send router solicitation message after ifconfig down/up command. For some reason it is not working. I set sysctl autoconf parameter to 1, but still after interface goes up ubuntu does not send RS message

/ thanks

---

### Post by lemming465 on 2012-11-24
What happens with *rdisc6* from userspace?  E.g.```
sudo -i
apt-get install ndisc6
rdisc6 eth0
```
Also could we see the output of```
ip address show
ip maddress show
ip -4 route show
ip -6 route show
```
We'll need more information to distinguish between possibilities like ipv6 isn't installed in the kernel, ipv6 was turned off at boot, ipv6 is on, but there are no ipv6 routers responding on ff02::2, and so on.  Is the problem unique to ubuntu?  What version of ubuntu?  What's the host hardware, particularly the NIC?  What's the network topology?

---

