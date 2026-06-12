---
title: "Subnetting question"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Nimbu on 2011-07-16
I want to set up to separate networks at home. I want to achieve a home network where a computer on subnet X can not communicate with a computer on subnet Y. 

1. Would I have to set up this configuration for each computer separately (cant find any relevant settings in my router)?
2. The router also needs an IP address and a subnet mask, will one router be able to manage 2 subnets and keep them separate?

3.Would these sample settings work?

PC1:SUBNET X                    
ip: 192.168.1.5                 
subnet mask: 255.255.255.0      
default gateway: 192.168.1.1    

PC2: SUBNET Y
ip: 192.168.1.195 
subnet mask: 255.255.255.192
default gateway: 192.168.1.1

Do I have the right idea here? Please help me out if I'm doing something wrong

Router = vodafone huawei HG556a

---

### Post by jmoorse on 2011-07-16
No that will not work.  You will need two different IP addresses (read: different interface or vlan) on the router to create 2 different networks.

Plus the second IP address/gateway is invalid (gateway needs to be in the subnet range, 192.168.1.195 / 255.255.255.192 = 192.168.1.192-255)

It doesn't look like your router supports this, but I have never worked with one of these models.

Why do you want the networks separate?

---

### Post by karlson on 2011-07-16
> **Nimbu said:**
> I want to set up to separate networks at home. I want to achieve a home network where a computer on subnet X can not communicate with a computer on subnet Y. 

1. Would I have to set up this configuration for each computer separately (cant find any relevant settings in my router)?


Unless your router is capable of supporting multiple internal IP addresses.

> 
2. The router also needs an IP address and a subnet mask, will one router be able to manage 2 subnets and keep them separate?


Not all of them.  It needs to be able to support multiple internal addresses or VLANs.

> 

3.Would these sample settings work?

PC1:SUBNET X                    
ip: 192.168.1.5                 
subnet mask: 255.255.255.0      
default gateway: 192.168.1.1    

PC2: SUBNET Y
ip: 192.168.1.195 
subnet mask: 255.255.255.192
default gateway: 192.168.1.1


Not it will not work as you show that you don't understand what subnets are.  Subnetting Y to 192 will prevent the computer from seeing the router.

Internet (IP4) addresses are 4 bytes representing a single integer and the subnet mask is &'d with the IP address to get a subnet ID.

So with your set up host X and host Y are on the same subnet.

> 
Do I have the right idea here? Please help me out if I'm doing something wrong

Router = vodafone huawei HG556a


You will need a set up like this you will need set like this:

```

PC1:SUBNET X                    
ip: 192.168.1.5                 
subnet mask: 255.255.255.0      
default gateway: 192.168.1.1    

PC2: SUBNET Y
ip: 192.168.2.5 
subnet mask: 255.255.255.0
default gateway: 192.168.2.1

```

---

### Post by SeijiSensei on 2011-07-17
Your best bet is to use three network cards in a single Linux box.  Set eth0 to obtain an address from the router with DHCP, then use static addresses for eth1 on, say, 192.168.10.0/24, and for eth2 on 192.168.20.0/24.  

By default Ubuntu won't pass any traffic between these networks because IP forwarding is disabled in /etc/sysctl.conf.  However it also won't forward traffic to the Internet either.  So you'll need to follow the instructions in that file to enable IP forwarding, then use iptables to create firewalling rules.  Something like this:

```

iptables -A FORWARD -i eth1 -o eth2 -j REJECT
iptables -A FORWARD -i eth2 -o eth1 -j REJECT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

---

### Post by Nimbu on 2011-07-17
Thanks karlson its clearer to me now.

---

