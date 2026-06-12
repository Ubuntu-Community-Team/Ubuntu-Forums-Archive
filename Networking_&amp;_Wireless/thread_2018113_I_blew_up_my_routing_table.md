---
title: "I blew up my routing table"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by sona1111 on 2012-07-06
HI a few days ago i was messing with ip routes in my endless attempts to get something working. (see the other thread i made) after many failures i asked someone on the #netfilter channel if they knew what i could do to set everything back to default. he said "ip rule flush". so i did that and now i am here. 

None of the network connections in the server work correctly, so as a first question, is their a connand to restore all the routing table ip routes and rules to what they were when i installed ubuntu? that would be the easiest. 

Failing that i may have found a piece of the problem. Route-n says:

Destination     Gateway         Genmask         Iface
192.168.3.0       0.0.0.0         255.255.255.0    br0

But i know their is supposed to be another thing there for the reverse direction, how can i add it back?

thanks.

---

### Post by sona1111 on 2012-07-06
bump

---

### Post by SeijiSensei on 2012-07-06
Did you try simply rebooting or restarting the network with "sudo service networking restart"?

---

### Post by sona1111 on 2012-07-06
yes

---

### Post by sona1111 on 2012-07-06
actually i use sudo /etc/init.d/networking restart

the one you suggested gives an "unknown instance" rebooting does not work either.

also when i do "sudo ip route add default via 192.168.3.1" it gives a 
RNETLINK answeres: no such process"

what does this error even mean?

---

### Post by SeijiSensei on 2012-07-06
Are you using static IPs or DHCP?  If the latter, restarting the network should have restored the correct routing table.  If you have a static configuration, there should be a "gateway" directive in /etc/network/interfaces for this interface.

Let's start with some basics.  If you run ifconfig, do you see the local network interface with an IP address in the 192.168.3.0/24 subnet?

Also I see you have a br0 interface.  Why are you using bridging?

---

### Post by sona1111 on 2012-07-06
seeing theirs no simple solution, ill get to the technical stuff.

ifconfig:
```
br0       Link encap:Ethernet  HWaddr 00:11:0a:5a:f1:b8
          inet addr:192.168.3.82  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:986337 (986.3 KB)  TX bytes:31159 (31.1 KB)

eth3      Link encap:Ethernet  HWaddr 00:11:0a:5c:22:29
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2880 (2.8 KB)  TX bytes:11940899 (11.9 MB)

eth4      Link encap:Ethernet  HWaddr 00:11:0a:5a:f1:b8
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:303548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:614259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:46424286 (46.4 MB)  TX bytes:585433221 (585.4 MB)

eth5      Link encap:Ethernet  HWaddr 00:11:0a:5a:f1:b9
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth8      Link encap:Ethernet  HWaddr 00:11:0a:5c:23:14
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1619857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1298449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1631555150 (1.6 GB)  TX bytes:187037996 (187.0 MB)

eth9      Link encap:Ethernet  HWaddr 00:11:0a:5c:23:15
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:966784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:155639917 (155.6 MB)  TX bytes:1076362937 (1.0 GB)

eth11     Link encap:Ethernet  HWaddr 00:02:a5:4e:35:b8
          inet addr:192.168.2.80  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe4e:35b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:6889 (6.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:125171 (125.1 KB)  TX bytes:125171 (125.1 KB)

```

Interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#secondary loopback
#auto lo: 1
#iface lo: 1 inet static
#address 192.168.0.1
#netmask 255.255.255.255

# List of Network interfaces (hot plug)

#Comcast Internet / Voip
auto eth9
iface eth9 inet manual
up ip link set eth9 up

#gigabit output
auto eth4
iface eth4 inet manual
up ip link set eth4 up

#main output
auto eth3
iface eth3 inet manual
up ip link set eth3 up

#RSAII
auto eth8
iface eth8 inet manual
up ip link set eth8 up

#AUX bridged connection 1
auto eth5
iface eth5 inet manual
up ip link set eth5 up

#main bridge
auto br0
iface br0 inet static
address 192.168.3.82
netmask 255.255.255.0
network 192.168.3.0/24
gateway 192.168.3.1
dns-nameservers 8.8.8.8
dns-search gamefaqs.com
bridge_ports eth9 eth4 eth3 eth8 eth5
bridge_fd 0
bridge_hello 2
bridge_maxage 12
bridge_stp on
#pre-up ip link set eth9 down
#pre-up ip link set eth4 down
#pre-up ip link set eth3 down
#pre-up ip link set eth8 down
#pre-up ip link set eth5 down
#pre-up brctl addbr br0
#pre-up brctl addif br0 eth9 eth4 eth3 eth8 eth5
#pre-up ip addr flush dev eth9
#pre-up ip addr flush dev eth4
#pre-up ip addr flush dev eth3
#pre-up ip addr flush dev eth8
#pre-up ip addr flush dev eth5
#post-down ip link set eth9 down
#post-down ip link set eth4 down
#post-down ip link set eth3 down
#post-down ip link set eth8 down
#post-down ip link set eth5 down
#post-down ip link set br0 down
#post-down brctl delif br0 eth9 eth4 eth3 eth8 eth5
#post-down delbr br0


#torrent downloader
#auto eth11
#iface eth11 inet static
#address 192.168.2.80
#gateway 192.168.2.4
#netmask 255.255.255.0
```

I have also tried setting the br0 interface down and setting the internet port (eth9) a static ip and setting the default route to the gateway 192.168.3.1. It still gives a "no such process" error and fails to ping. (network unreachable)

As you can see their is a gateway directive, but i can try dhcp if you think that would help. (ill need it to be static in the future though) 

The br0 is for bridging. As far as i have seen in the 6 months i have used the server so far, the br0 basically takes the place of the internet interface when set up this way. It just acts as a simple network switch to the other devices. 

thanks for reading.

---

### Post by SeijiSensei on 2012-07-06
deleted; see below

---

### Post by SeijiSensei on 2012-07-06
OK, so the br0 interface points to the Internet or at least to some upstream router?  Is the issue routing from 192.168.2.0/24 network to the upstream gateway?

You should see two routes by default when the network interfaces are brought up.  There should be a route to the 192.168.2.0/24 network on eth11, and a route for the 192.168.3.0/24 network on br0.  If the br0 interface is the one pointing upstream, you'd need a 

```
/sbin/ip route add default via 192.168.3.1
```

presuming 192.168.3.1 is the IP address of the upstream router on the br0 side. If you then run "route -n" you should see:

```

0.0.0.0       192.168.3.1     0.0.0.0         UG    0      0        0 br0
192.168.3.0   0.0.0.0         255.255.255.0   U     2      0        0 br0
192.168.2.0   0.0.0.0         255.255.255.0   U     2      0        0 eth11
```

Since this was working before, I presume you already enabled packet forwarding by setting net.ipv4.ip_forward=1 in /etc/sysctl.conf.

---

### Post by sona1111 on 2012-07-06
Thank you again for the reply. 

First of all im sorry i even included eth11 in the picture, it was part of a project i was working which got me into this mess, but before i do anything i just want to get br0 working correctly again. For now just assume eth11 does not exist, i will set it down. 

br0 connects to a standard linksys router which then connects to the cable modem. 

for the route -n i am missing the return route:

```

192.168.3.0   0.0.0.0         255.255.255.0   U     2      0        0 br0
192.168.2.0   0.0.0.0         255.255.255.0   U     2      0        0 eth11
```

as i stated two posts ago, i have already tried to add the correct route with 

```
sudo ip route add default via 192.168.3.1
```

(i also just tried it again with the /sbin/) which gives a "RNETLINK answers: No such Process" error. very mystifying.

---

### Post by SeijiSensei on 2012-07-07
Well, I'm out of solutions for now.  I never use bridging, so I can't tell whether your use of it here is the root cause of the problem.  Can you ping the router at 192.168.3.1?  Is there any way you can configure this machine to use only Ethernet interfaces and get rid of the bridge?

---

### Post by sona1111 on 2012-07-07
well i was really pulling out my hair over this one but i finally found a working "solution". Whatever the problem was it was some rule pointing to br0, so just changing the interfaces file to call it br1 and rebooting the machine fixed it. 

It still bugs me in the back of my mind that i could not actually "fix" it, but oh well.

---

