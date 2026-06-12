---
title: "Host can't access gateway but VM can with Bridged Networking"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by EdCostello on 2011-06-19
I've set up bridged networking so that I can have KVM virtual machines that are accessible from outside the host. I can access both the Host and my VM from other machines on the local network, and from the VM I can access the internet but from the Host I can only access my local network. Since I can access the local network and the same issue applies regardless of whether I use host names or IP addresses I suspect it's not picking up the gateway properly.

How do I go about allowing the VM host to access the internet while still having bridged networking so I can access my VMs?

What I've checked so far:
**Ping Google DNS (8.8.8.8 )**
From Host: Destination Host Unreachable
From VM: Suceeds

**tracepath 8.8.8.8 -n**
From Host:
 ```
1:  192.168.1.15                                          0.215ms pmtu 1500
 1:  192.168.1.15                                        3001.013ms !H
     Resume: pmtu 1500
```

From VM:
```
 1:  192.168.1.1                                           7.055ms asymm  2 
 2:  203.109.128.90                                       59.708ms 
 3:  203.109.143.101                                     149.582ms
... More
```

Since 192.168.1.1 is my NAT gateway the VM is clearly going straight to gateway and out as would be expected, but the Host (IP 192.168.1.15)  seems to be not leaving the box.

**route -n**
From Host:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 br0
```

I'm not realy sure how to intepret this, but it does look to me like it's picked up the gateway properly.

/etc/network/interfaces on the Host is as follows:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 9
	bridge_maxwait 0
```

I've also checked that the DNS specified in /etc/resolve.conf is correct. But since things fail using IP addresses that's unlikely to be the cause.

The issues are only with accessing things outside of my subnet. I can access other machines on the same subnet from the Host just fine.

---

### Post by xueliangfei on 2011-09-19
i encouter the same problem 
i can not solve it either
can you help 
 
any help is welcome
 thanks in advance!

---

### Post by xueliangfei on 2011-09-19
> **EdCostello said:**
> I've set up bridged networking so that I can have KVM virtual machines that are accessible from outside the host. I can access both the Host and my VM from other machines on the local network, and from the VM I can access the internet but from the Host I can only access my local network. Since I can access the local network and the same issue applies regardless of whether I use host names or IP addresses I suspect it's not picking up the gateway properly.
 
How do I go about allowing the VM host to access the internet while still having bridged networking so I can access my VMs?
 
What I've checked so far:
**Ping Google DNS (8.8.8.8 )**
From Host: Destination Host Unreachable
From VM: Suceeds
 
**tracepath 8.8.8.8 -n**
From Host:
```
1:  192.168.1.15                                          0.215ms pmtu 1500
 1:  192.168.1.15                                        3001.013ms !H
     Resume: pmtu 1500
```
 
From VM:
```
 1:  192.168.1.1                                           7.055ms asymm  2 
 2:  203.109.128.90                                       59.708ms 
 3:  203.109.143.101                                     149.582ms
... More
```
 
Since 192.168.1.1 is my NAT gateway the VM is clearly going straight to gateway and out as would be expected, but the Host (IP 192.168.1.15) seems to be not leaving the box.
 
**route -n**
From Host:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 br0
```
 
I'm not realy sure how to intepret this, but it does look to me like it's picked up the gateway properly.
 
/etc/network/interfaces on the Host is as follows:
```
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp
 
auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 9
    bridge_maxwait 0
```
 
I've also checked that the DNS specified in /etc/resolve.conf is correct. But since things fail using IP addresses that's unlikely to be the cause.
 
The issues are only with accessing things outside of my subnet. I can access other machines on the same subnet from the Host just fine.
 
 
 
Do you solve the problem?

---

### Post by xueliangfei on 2011-09-22
UP 
 
problem unsolved
 
keep on asking for help

---

