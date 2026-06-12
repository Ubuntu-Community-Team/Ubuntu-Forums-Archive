---
title: "Route related issues."
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2011-09-13
Hi,

I have a strange issue with my routing table. My topology is

host --- router --- internet

Router has two nic cards .. one towards host has ip 192.168.0.1 and host has 192.168.0.2. Eventhough I am not setting the default route it is taking 192.168.0.1 as default route

On my router if I check the routing table it is set as shown below

```
# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

That sounds stupid as my ETH0 ip is 192.168.0.1 and it is taking the same as default gateway .. Any reason why it is happening so ?

---

### Post by Grenage on 2011-09-14
> **codingfreak said:**
> Hi,

I have a strange issue with my routing table. My topology is

host --- router --- internet

Router has two nic cards .. one towards host has ip 192.168.0.1 and host has 192.168.0.2. Eventhough I am not setting the default route it is taking 192.168.0.1 as default route

On my router if I check the routing table it is set as shown below

```
# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```

That sounds stupid as my ETH0 ip is 192.168.0.1 and it is taking the same as default gateway .. Any reason why it is happening so ?

I'm not sure what you see as a problem; that looks normal to me.

---

### Post by SeijiSensei on 2011-09-14
The interface that points to the Internet should have the public IP assigned by your provider, and the default gateway should be the ISP's next-hop router upstream.

---

