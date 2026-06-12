---
title: "Forward port to virtual kvm guest"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by Empire-Phoenix on 2012-01-21
Well I have a machine with a kvm guest(ubuntu as well but shouldn't matter), useing user-networking. 
The current address of the physical machine is 192.168.3.56, however this one will change later. 

The virtual machine is 192.168.122.158, 
the virtual machine can connect to the internet using masquerading, that part works well. Now I changed in the ssh config the ssh server of the virtual machine to port 222 and want to be able to connect ot that from the outside -> ssh 192.168.3.56 -p 222 
I added the rule to iptables on the physical machine (see below)
Now I get a connection timed out instead of a connection denied, however it does not work as expected. 
I really can't see what I'm doing wrong, any help would be appreciated.



```

remote@Empire-Server:~$ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  anywhere             anywhere            tcp dpt:222 to                                                                                          :192.168.122.158:222

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  tcp  --  192.168.122.0/24    !192.168.122.0/24    masq ports: 1                                                                                          024-65535
MASQUERADE  udp  --  192.168.122.0/24    !192.168.122.0/24    masq ports: 1                                                                                          024-65535
MASQUERADE  all  --  192.168.122.0/24    !192.168.122.0/24
remote@Empire-Server:~$

```

```

remote@Empire-Server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:4f:2e:5c
          inet addr:192.168.3.56  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe4f:2e5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:205295759 (205.2 MB)  TX bytes:47058283 (47.0 MB)
          Interrupt:40 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:335130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:348277247 (348.2 MB)  TX bytes:348277247 (348.2 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:a6:2b:8c
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4108123 (4.1 MB)  TX bytes:199746231 (199.7 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:a6:2b:8c
          inet6 addr: fe80::fc54:ff:fea6:2b8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:5105167 (5.1 MB)  TX bytes:199823562 (199.8 MB)

```

---

### Post by Empire-Phoenix on 2012-01-21
Oh .. I finally found a solution. Always TRY to do a iptables --flush, before testing if it works.! Hope this saves some other people reading this trouble.

---

