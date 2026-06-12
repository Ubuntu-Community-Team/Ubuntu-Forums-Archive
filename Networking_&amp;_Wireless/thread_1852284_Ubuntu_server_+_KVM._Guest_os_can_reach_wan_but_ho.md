---
title: "Ubuntu server + KVM. Guest os can reach wan but host machine cannot"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by xueliangfei on 2011-09-29
Hi there. I have a strange problem here. I've set up ubuntu server 10.04 x64 with kvm and bridged networking and installed win server 2008 as a guest os. The guest os has full access to the network including lan/wan but the host os can only reach my lan and not the wan. This is true even when the guest machine is powered off?

I have to admit that my knowledge of networking, particularly with respect to linux is very flakey but surely if the guest has internet access this should also apply to the host? My only suggestion is an issue with mac addresses but i don't know where to start. Has anybody ran into this problem before?

Thanks
[IMG]http://blog.chinaunix.net/attachment/201109/30/26284395_1317346754K6WH.jpg[/IMG]

---

### Post by judoka9999 on 2011-09-29
Please send the output of the command:
route print

from the Windows Guest, and the output of:

ip route list

from the Linux host.

**EDIT, feel free to obfuscate public IPs. Just substitute bogon (10.Anything.Anything.Anything), but be consistent. Have exactly one bogus substitute address for each address you wish to obfuscate, and use it every time that address comes up. This will still allow me to get an accurate picture.

---

### Post by xueliangfei on 2011-09-29
> **judoka9999 said:**
> Please send the output of the command:
route print
 
from the Windows Guest, and the output of:
 
ip route list
 
from the Linux host.
 
**EDIT, feel free to obfuscate public IPs. Just substitute bogon (10.Anything.Anything.Anything), but be consistent. Have exactly one bogus substitute address for each address you wish to obfuscate, and use it every time that address comes up. This will still allow me to get an accurate picture.
 
 
thanks very much 
i think i have already show the public IP in the picture1  so i will not obfuscate it anymore. 
[IMG]http://blog.chinaunix.net/attachment/201109/30/26284395_1317348318H785.jpg[/IMG]
what information else will you need
i have to say here the gateway is not 58.194.170.254 
but when i use the real gateway such as 202.194.20.254 (it is not in the same range with the ip)  the br0 can not be restart. It will show a error
what can i do ?
Thanks

---

### Post by judoka9999 on 2011-09-29
If the guest can browse, but the host cannot, I wish to examine both of their routing tables. If the guest has a bridged network to the host's NIC, then they should be using the same gateway.

**EDIT, In either case, knowing what routing table actually works will shed some light on the situation. If we see internal IPs for the default gateway on the guest then we know some NAT is going on at a host level.

---

### Post by xueliangfei on 2011-09-29
> **judoka9999 said:**
> If the guest can browse, but the host cannot, I wish to examine both of their routing tables. If the guest has a bridged network to the host's NIC, then they should be using the same gateway.
 
**EDIT, In either case, knowing what routing table actually works will shed some light on the situation. If we see internal IPs for the default gateway on the guest then we know some NAT is going on at a host level.
 
Thanks ,Im sorry.I can not catch your idea clearly. All the VM is using the bridge of the host to get to the internet access successfully. But the problem is the host can not.
Im sure the VM is using the bridge method.

---

### Post by judoka9999 on 2011-09-29
So, does the host's routing table match the guest's? If not, adjust the network configuration on the host to match that of the guest.

---

### Post by xueliangfei on 2011-09-29
> **judoka9999 said:**
> So, does the host's routing table match the guest's? If not, adjust the network configuration on the host to match that of the guest.
 
 
Yes , these is some different.
This is the route table in the vm 
[IMG]http://blog.chinaunix.net/attachment/201109/30/26284395_1317351237WJxx.jpg[/IMG]
you can see the different between the host machine

---

### Post by judoka9999 on 2011-09-29
I thought the guest was Windows Server 2008?

In any case, they are both using the same default gateway. The 169.254 address is an address for an interface that wasn't getting a response on DHCP.

what do your iptables rules look like on the host? Look at:
sudo iptables -L -n -v

and:
sudo iptables -t nat -L -n -v

---

### Post by xueliangfei on 2011-09-30
> **judoka9999 said:**
> I thought the guest was Windows Server 2008?
 
In any case, they are both using the same default gateway. The 169.254 address is an address for an interface that wasn't getting a response on DHCP.
 
what do your iptables rules look like on the host? Look at:
sudo iptables -L -n -v
 
and:
sudo iptables -t nat -L -n -v
 
Oh , it is  the test machine of ubuntu
 
iptables rules  can tell us about what?
 
thanks in advance.

---

### Post by xueliangfei on 2011-09-30
> **judoka9999 said:**
> So, does the host's routing table match the guest's? If not, adjust the network configuration on the host to match that of the guest.
 
 
Ok  I  will try it and tell your the result 
 
thanks

---

### Post by judoka9999 on 2011-09-30
If the routing tables are the same and it's still not working the next logical place to check are the iptables rules. The host's iptables rules won't apply to a bridged guest (at least I don't think, I'm more a VMware guy than KVM.) The host's iptables rules however, could prevent it from accessing the Internet.

---

