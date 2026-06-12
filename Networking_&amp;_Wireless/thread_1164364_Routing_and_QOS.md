---
title: "Routing and QOS"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by serafettin on 2009-05-19
Hi everybody,

For my thesis I have to configure ubuntu as a router. I want to use like this, 
1 PC as a router (ubuntu) (2 ethernet cards)
2 Laptops as a clients
(and network must be IPv6 actualy)

And I have to start, data and multicast traffic one laptop to another. The multicast traffic will be send by VLC player. The data traffic would fill all the bandwith (it can be ftp traffic) So i have to show that when priotization active the multicast continues without any problem, and when there is no priotization the video will down or broken.

So I am new on linux and i have read already all of the LARTC documents but I cant make the configurations. 

So can anyone please help?

---

### Post by puppywhacker on 2009-05-19
TC is your friend. but your setup is flawed the traffic shaping takes place only on the router. QoS works best on the egress of the congested node. you can tag the traffic on the source but it's up to each node to implement an expediting queue. Usually shaping halfway has little effect.

---

### Post by serafettin on 2009-05-20
tahnk you puppywhacker; 

i'll try tc but my problem is that i can't configure the network, i mean i can't start  the qos step yet. 

How do i configure for IPv6 and my ubuntu become a IPv6 router?

---

### Post by puppywhacker on 2009-05-20
first assign site local addresses to all hosts.
then on the router set the ip_forwarding for ipv6 to true, otherwise it is an end-point in ip communication and can't forward the packets. next make sure you can route properly between the two laptops, you may need to add routes on the router to the laptops and make sure the default gateway on the laptop is routing to the router. Mind you that there are multiple setups possible. below are a few commands to play with... I didn't fully think it over, but hey, it's your project anyway =)

ROUTER
ip addr add fec0::1 dev eth0
ip addr add fec0::2 dev eth1
sysctl -w net.ipv6.conf.all.forwarding=1
ip route add fec0::3 via dev eth1
ip route add fec0::4 via dev eth0

---

