---
title: "Unable to ping6 on ipv6 interface"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by kaylessa on 2013-04-12
Hi guys,

I have a problem over here in which i am unable to ping6 my own interface. Rebooting the server , restarting the interface doesnt help. It is in a vmware container.


eth1      Link encap:Ethernet  HWaddr 00:0c:29:37:b0:a2
            inet6 addr: 2000:1234:5678:9abc::1:100/64 Scope:Global
          inet6 addr: fe80::20c:29ff:fe37:b0a2/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:388176 errors:46 dropped:36 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:112828620 (112.8 MB)  TX bytes:892 (892.0 B)
          Interrupt:19 Base address:0x2080

PING 2000:1234:5678:9abc::1:100(2000:1234:5678:9abc::1:100) 56 data bytes
From ::1 icmp_seq=1 Destination unreachable: Address unreachable
From ::1 icmp_seq=2 Destination unreachable: Address unreachable
From ::1 icmp_seq=3 Destination unreachable: Address unreachable

---

### Post by sanderj on 2013-04-12
Can you ping6 the fe80 address?

And: have you really set the address  2000:1234:5678:9abc::1:100?

---

### Post by kaylessa on 2013-04-12
#ping6 fe80::20c:29ff:fe37:b0a2
connect: Invalid argument


this is my interfaces file.

auto eth0
iface eth0 inet dhcp
iface eth0 inet6 static
address 2000:1234:5678:9abc::1:100
netmask 64


this is not my first time setup for ipv6. previously it was working not sure why now it is not working.

---

### Post by sanderj on 2013-04-12
Aha. One step back: what is your goal with the "2000:1234:5678:9abc::1:100"?

---

### Post by kaylessa on 2013-04-12
my goal is to set up a ipv6 address and be able to ping6 it

---

### Post by sanderj on 2013-04-12
> **kaylessa said:**
> my goal is to set up a ipv6 address and be able to ping6 it

Then the following is easier:

```
sudo apt-get install miredo
```


That will give you a real, working IPv6 address which you can ping6.

HTH

---

### Post by kaylessa on 2013-04-12
no it doesnt make sense. i just want to set up a private network with just two computer. Why cant i ping my own ipv6 interface?

---

### Post by sanderj on 2013-04-12
For a private network, the FE80 address is enough. In the ping6, you have to specify the interface. (man ping6)

---

### Post by kaylessa on 2013-04-12
why need a private address unless you are saying at OS level it will drop 2000: network?

The thing i understand is it work previously now it doesnt work.

---

### Post by sanderj on 2013-04-12
> **kaylessa said:**
> why need a private address unless you are saying at OS level it will drop 2000: network?

The thing i understand is it work previously now it doesnt work.

If you want to ping6 between computers with your own address space 2000::, your system needs to know the network mask or routing table. Check with "ip -6 route show". So that's more difficult than using fe80 or installing miredo. That's why I advice the latter row.

If it worked, just think what you've done since then, or do a restore from your backup.

---

### Post by kaylessa on 2013-04-12
the strange thing is i have many ubuntu machine on my windows vmware. and all is not working.

strange enough i cant even ping my link local o.O

i installed miredo on two machines. It cannot ping one another o.O. ufw is stop.

---

### Post by sanderj on 2013-04-12
> **kaylessa said:**
> the strange thing is i have many ubuntu machine on my windows vmware. and all is not working.

well, that's at least consistent. ;)

---

