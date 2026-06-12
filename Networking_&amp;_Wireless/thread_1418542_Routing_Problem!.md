---
title: "Routing Problem!"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by ricker_699 on 2010-02-28
Hello,
 
I am fairly new to the Linux world and could use some help. I am attempting to create a router for a remote location. I'll try to give as much information as I can here. I am running this in Ubuntu 6.10
 
Here is my set up:
 
Router A:
eth0 address 192.168.78.30 netmask 255.255.255.0
eth1 address 172.16.6.1 netmask 255.255.255.0
 
Routing Table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.6.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
10.0.0.0 172.16.6.1 255.255.255.0 UG 0 0 0 eth1
192.168.78.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 172.16.6.254 255.255.255.0 UG 0 0 0 eth1
 
Router B:
eth0 address 10.0.0.15 netmask 255.255.255.0
eth1 address 172.16.6.2 netmask 255.255.255.0
 
Routing Table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.6.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
10.0.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.78.0 172.16.6.1 255.255.255.0 UG 0 0 0 eth1
0.0.0.0 172.16.6.254 0.0.0.0 UG 0 0 0 eth1
 
Two laptops set up statically (this is simply for testing right now)
 
Laptop A:
IP Address: 192.168.30.78
Mask: 255.255.255.0
Default Gateway: 192.168.78.30
 
Laptop B:
IP Address: 10.0.0.15
Mask: 255.255.255.0
Default Gateway: 10.0.0.15
 
Problem:
I am able to ping between the Routers on the Router level (i.e. from Router A I can ping 10.0.0.15 and 172.16.6.2 on Router B. From Router B I am able to ping 192.168.78.30 and 172.16.6.1 on Router A).
 
From my laptops I am able to ping up to the router they are connected to (i.e. from Laptop A I can ping 192.168.78.30 and 172.16.6.1 and from Laptop B I can ping 10.0.0.15 and 172.16.6.2).
 
What I CANNOT do is ping anything on Router B from Laptop A (i.e. I cannot ping 10.0.0.15 or 172.16.6.2 from Laptop A. I cannot ping 192.168.78.30 or 172.16.6.1 from Laptop B).
 
Obviously this is a problem. I'm not the strongest in networking so any help that you can give me I would appreciate greatly. I need to be able to ping through the routers and ping the other networks on the PC level (not sure why I can do it at the Router level and not the PC level). Thanks in advance.
 
Rick

---

### Post by lloyd_b on 2010-03-01
> Router A:
eth0 address 192.168.78.30 netmask 255.255.255.0
eth1 address 172.16.6.1 netmask 255.255.255.0

Routing Table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.6.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
10.0.0.0 [COLOR="Red"]172.16.6.1[/COLOR] 255.255.255.0 UG 0 0 0 eth1
192.168.78.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 172.16.6.254 255.255.255.0 UG 0 0 0 eth1

Router B:
eth0 address 10.0.0.15 netmask 255.255.255.0
eth1 address 172.16.6.2 netmask 255.255.255.0

Routing Table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.6.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
10.0.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.78.0 172.16.6.1 255.255.255.0 UG 0 0 0 eth1
0.0.0.0 172.16.6.254 0.0.0.0 UG 0 0 0 eth1I believe the gateway in red above should be pointing to 172.16.6.2, rather than 172.16.6.1
> Laptop A:
IP Address: 192.168.30.78
Mask: 255.255.255.0
Default Gateway: 192.168.78.30

Laptop B:
IP Address: 10.0.0.15
Mask: 255.255.255.0
Default Gateway: 10.0.0.15The IP addresses you list for these two can't be right.  The first one looks like the last two numbers are transposed, and they conflict with the gateway IP addresses anyway.

I'm guessing that these are just typos.  But when sorting out a routing problem, typos can make it VERY difficult for us to understand what's going on.

Could you please verify all the info, and repost it (assuming that gateway issue I pointed out is in fact a typo and not the cause of your problem).

Lloyd B.

---

### Post by ricker_699 on 2010-03-02
Thanks for your response, I'll try changing the 172.16.6.1 to 172.16.6.2 as suggested tonight when I get home.  The other items that you referred to are in fact typos...I got a little a head of myself and pressed for time.  The IP addresses for the laptops are actually as follows:
 
Laptop A: 192.168.78.45
Laptop B: 10.0.0.100
 
Not sure how I came up with those other addresses other than the fact that they are the gateways, but thanks for pointing that out to me in my original post.  I will reply again tonight after making the gateway change to let you know if that resolved the issue or not.
 
Unfortunately my remote location has opted to purchase a Cisco and spend the big money, however I'd still like to get this working for personal gain.
 
Although new to linux I must say that I am very impressed with everything that it can do.  Thank you again for your reply and I'll let you know how things go tonight.

---

