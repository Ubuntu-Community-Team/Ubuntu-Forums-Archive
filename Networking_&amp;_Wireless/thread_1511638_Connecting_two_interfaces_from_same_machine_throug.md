---
title: "Connecting two interfaces from same machine through a gateway"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by minuta on 2010-06-17
I am trying to make a comparison test between two different   Packet Filters implementations and I want to use the following testbed  :only two machines with 2 interface cards each
1-->sender(eth0 192.168.3.2)-receiver(eth1 192.168.4.2)  machine;forwarding is disabled for this machine;Ubuntu9.10
2-->and gateway(wm0 192.168.4.1; wm1 192.168.3.1);forwarding is  enabled
 
  The problem is I don't manage to obtain a correct configuration:when I  try to ping from sender interface to receiver interface through the  gateway
I can see with wireshark the requests on the receiver [URL="http://www.linuxforums.org/forum/#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]interface[/FONT][/FONT][/COLOR][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL],but this interface is not replying  in turn.
 ping -I eth0 192.168.4.2 or  ping -I eth1 192.168.3.2 have the same  behaviour as explained up
 
Any information would be very useful.Thank you[IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG]

---

### Post by firewrks on 2010-06-17
More than likely Machine A's routing table is attempting to route back to it's self.  

Try posting the output of:
route -v
ping -l eth0 192.168.3.1
ping -l eth0 192.168.4.1

My guest is the last ping may fail depending on the routing setup.

---

### Post by minuta on 2010-06-18
> **firewrks said:**
> More than likely Machine A's routing table is attempting to route back to it's self.  

Try posting the output of:
route -v
ping -l eth0 192.168.3.1
ping -l eth0 192.168.4.1

My guest is the last ping may fail depending on the routing setup.

The routing table for the first machine looks like this:
root@dragos-desktop:/home/dragos# route -v
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     *               255.255.255.0   U     0      0        0 eth0
192.168.4.0     *               255.255.255.0   U     0      0        0 eth1
link-local         *               255.255.0.0      U     1000   0        0 eth1
default         192.168.4.1     0.0.0.0         UG    100    0        0 eth1
default         192.168.3.1     0.0.0.0         UG    100    0        0 eth0

ping -I eth0 192.168.3.1 works fine

ping -I eth0  192.168.4.1  is not working even in wireshark,on eth0, I can see both request and reply

7       2.999945         192.168.3.2           192.168.4.1          ICMP    Echo (ping) request
8        3.000763       192.168.4.1             192.168.3.2          ICMP    Echo (ping) reply

9        4.003965         192.168.3.2         192.168.4.1            ICMP    Echo (ping) request
10    4.004514         192.168.4.1          192.168.3.2           ICMP    Echo (ping) reply

---

