---
title: "UFW allowing IP range"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by skyraider7 on 2009-10-25
Hi,
 
I want to allow any IP range, let's say from 123.45.0.0 to 123.45.255.255. There seems to be a way to allow any number zero through 255 in the last block by typing "0/24". But I see no way to do the same for the third block. I'm so confused... there seem to be no wildcards in UFW and I just can't figure this out.
 
I tried adding the following:
 
ufw allow proto tcp from 123.45.0.0/123.45.255.255 to any port 22
 
... above my first rule, which is:
 
ufw deny proto tcp from any to any port 22
 
... but was denied access.
 
Any ideas?
 
Thanks!

---

### Post by mr_steve on 2009-10-25
> **skyraider7 said:**
> Hi,
 
I want to allow any IP range, let's say from 123.45.0.0 to 123.45.255.255. There seems to be a way to allow any number zero through 255 in the last block by typing "0/24". But I see no way to do the same for the third block. I'm so confused... there seem to be no wildcards in UFW and I just can't figure this out.
 
I tried adding the following:
 
ufw allow proto tcp from 123.45.0.0/123.45.255.255 to any port 22
 
... above my first rule, which is:
 
ufw deny proto tcp from any to any port 22
 
... but was denied access.
 
Also, why could I not figure this out - what additional knowledge would I have needed to understand the solution, considering that IP ranges like this are not explained in the manual?
 
Thanks!

The /24 at the end of the address is the network mask, in CIDR notation. You can look up netmask calculators to figure out what it means, but basically /24 means a netmask of 255.255.255.0

If I understand your problem correctly, you want a netmask of 255.255.0.0, so you would use 123.45.0.0/16

---

### Post by Dark_Stang on 2009-10-25
The /24 is the subnet mask. Here is some reading for you...
[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

---

### Post by skyraider7 on 2009-10-25
> **mr_steve said:**
> The /24 at the end of the address is the network mask, in CIDR notation. You can look up netmask calculators to figure out what it means, but basically /24 means a netmask of 255.255.255.0
 
If I understand your problem correctly, you want a netmask of 255.255.0.0, so you would use 123.45.0.0/16
 
Cool.  That worked.
 
Reading up on subnets, CIDR etc.
 
Thanks.

---

