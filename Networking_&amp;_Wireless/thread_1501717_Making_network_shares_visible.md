---
title: "Making network shares visible"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by spxxn on 2010-06-04
Hello, I have a bit of a problem.  I am trying to make my network shares visible to other networks within the same subnet.  I am able to get to the server using the hostname but I want to be able to get to the machine's shares by using any of the virtual IP addresses that I've assigned it.  The I have four virtual addresses connected all within the same subnet.  I am in a corporate environment so I'm afraid access to the router is not an option.  I would appreciate any input.

Oh here is an example of what I'm looking at.

Primary IP 192.168.0.66 This is the primary address of the router I'm connecting to and this address will not ping the others from the server?

eth0.2 192.168.100.66
eth0.3 192.168.200.66
eth0.4 192.168.203.66

---

### Post by Jeroensum on 2010-06-05
And back to subnet-school you go young man!  :P

192.168.X.X is a class C subnet with a default mask of 255.255.255.0
You have created 4 ip's in 4 different subnets...

To correct the problem assign a different subnet or put all ip's in one of the subnets:
192.168.0.67
192.168.0.68
192.168.0.69
192.168.0.70

:)

---

### Post by capscrew on 2010-06-05
> **Jeroensum said:**
> And back to subnet-school you go young man!  :P

Pretty judgmental I would say.  You don't have enough information to make any statements about the OP or his network (i.e. what subnet mask is being used).> 

192.168.X.X is a class C subnet with a default mask of 255.255.255.0
You have created 4 ip's in 4 different subnets...

Who uses the term "Class C" anymore.  If the OP is using a perfectly legitimate 192.168.0.0/16 (255.255.0.0) network all of the addresses would be in the same subnet!.  There is no rule that says you have to use a 192.168.0.0/24 (255.255.255.0) network.> 

To correct the problem assign a different subnet or put all ip's in one of the subnets:
192.168.0.67
192.168.0.68
192.168.0.69
192.168.0.70
:)
I would assume you mean the subnet of 192.168.0.0/24 here. ;-)

---

### Post by capscrew on 2010-06-05
> **spxxn said:**
> Hello, I have a bit of a problem.  I am trying to make my network shares visible to other networks within the same subnet.  I am able to get to the server using the hostname but I want to be able to get to the machine's shares by using any of the virtual IP addresses that I've assigned it.  The I have four virtual addresses connected all within the same subnet.  I am in a corporate environment so I'm afraid access to the router is not an option.  I would appreciate any input.

Oh here is an example of what I'm looking at.

Primary IP 192.168.0.66 This is the primary address of the router I'm connecting to and this address will not ping the others from the server?

eth0.2 192.168.100.66
eth0.3 192.168.200.66
eth0.4 192.168.203.66

Tell us more about the network configuration.  What is the sumnet mask of the network?  How have you configured the "virtual interfaces" for the server?  Is this a Linux host? Can you provide the output of ```
ipconfig -a
cat /etc/network/interfaces
cat /etc/hosts
```

---

### Post by Jeroensum on 2010-06-12
> **capscrew said:**
> Tell us more about the network configuration.  What is the **sumnet mask** of the network?  How have you configured the "virtual interfaces" for the server?  Is this a Linux host? Can you provide the output of ```
ipconfig -a
cat /etc/network/interfaces
cat /etc/hosts
```

I think you mean **subnet mask** here, right? :biggrin:

Btw, it would be nice to know if this topic has been solved or not... TS, kindly place a [Solved] before the topic title to let us know. Also a reply how you fixed it would be nice :)

---

