---
title: "Tom"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by lkytmr on 2010-05-14
I am new to ubuntu and I am trying to configure a vmware virtual machine using ubuntu-10.04-server-i386.iso. I install it with lamp stack and it comes up fine. Ethernet works, can browse to the ip address and i see it works. everything fine. If I add anything to the system, sudo apt-get install openssh-server or do anything else and reboot, the network doesn't work.

Ifconfig shows 

eth 0 Link encap:Ethernet HWaddr 00:0c:29:51:a1:e0
      inet6 addr: fe80::20c:29ff:fe51:a1e0/64 cope:link ...

lo    Link encap:Local loopback
      inet addr: 127.0.0.1 Mask 255.0.0.0

I can ping 127.0.0.1
If I try to ping the host machine, I get a network is unreachable error like dhcp not functioning.

I can start over with a fresh machine and the same thing happens.

Any help would be appreciated.

Thanks loads
Tom :confused:

---

