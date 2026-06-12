---
title: "no network after using ip-netns (network namespace)"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by keqhe on 2013-07-15
Hello--

Today, I want to setup an experiment to transfer traffic between two NICs on the same OS (ubuntu12.04). The steps I followed are:


a.building two network namespaces:net0 and net1
b.ip netns add net0
c.ip netns add net1
d.ip netns list
e.ip link set eth0 netns net0
f.ip link set eth0 netns net1
g.ip netns exec net0 ip link set eth0 up
h.ip netns exec net1 ip link set eth1 up
i.ip netns exec net0 ip address add 10.0.1.1/24 dev eth0
j.ip netns exec net1 ip address add 10.0.1.2/24 dev eth1
k.ip netns exec net0 ping -c 3 10.0.1.2



After that, I performed:
ip netns delete net0
ip netns delete net1

And then I connect an Ethernet cable to a switch. Then I "edit the network" using the GUI located in the right up Conner of the desktop. 
I specified "auto DHCP", but there is no network connection. Before this experiment, it is fine.

I noticed that no light on the NIC is flickering (no red/green light on...)

Does anybody can help me and tell me what to do? Thanks!

---

