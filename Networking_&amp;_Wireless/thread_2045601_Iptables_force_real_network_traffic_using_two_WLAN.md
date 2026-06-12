---
title: "Iptables: force real network traffic using two WLAN adapters (no loopback bridging)"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by Skyo on 2012-08-21
Dear forum, 


my laptop has two network interfaces, 
one build-in (WLAN1) and another one attached via usb (WLAN2).


I am facing an inconvenient situation: I am performing quite often some network analysis. 
So I have to create real network traffic and mustnot use the loopback interface - but thats exactly what is happening.


```

Problem: Wlan1 -> loopback -> Wlan2 

Request: Wlan1 -> medium -> Wlan2, with medium!=loopback, 
working with variable networks

```So far, I've found some [related forum entries]("http://superuser.com/questions/241178/how-to-use-different-network-interfaces-for-different-processes"), but no real answer. Daniel Ryde uses a self developed code injection program. 
But these tools add only the functionality to choose a sender / source interface (IP address), but **NO** medium.
Reference: [http://superuser.com/questions/241178/how-to-use-different-network-interfaces-for-different-processes](http://superuser.com/questions/241178/how-to-use-different-network-interfaces-for-different-processes)


Can my request be accomplished via interfaces config file, iptables, routing entries (or some other well known unix tools)?




Thanks.:popcorn:

---

### Post by Skyo on 2012-08-29
Okay, so that is what I got and it is still not working.
I've managed to send packets with the correct interface,
over the network and receiving it with the correct interface.
I can see incoming packets while sniffing at the incoming interface. 
The packets are not answered / dropped, however.

I guess some kernel options drops the packets.

One option is  to set the interfaces in promiscous mode,
but that would cause far to much to handle...

```


# add routing rules into main routing table, so that the outgoing interface
# and source address is chosen correctly
sudo /bin/ip route add $interface_1_ip/32 dev $interface_2 src $interface_2_ip
sudo /bin/ip route add $interface_2_ip/32 dev $interface_1 src $interface_1_ip

# send a gratuitous ARP REPLY (-A), to tell other communication devices
# (e.g. switch) your IP / MAC combination
sudo /usr/bin/arping -c 4 -A -I $interface_1 $interface_1_ip
sudo /usr/bin/arping -c 4 -A -I $interface_2 $interface_2_ip
    
# remove locally hosted ip's from local routing table - doing this
# ensures, that the loopback device is not used
sudo /bin/ip route del $interface_1_ip table local
sudo /bin/ip route del $interface_2_ip table local

# arp requests will not be answered, as the machine guesses, that it
# does not possess the IP's - therefore add static ARP entries
sudo /usr/sbin/arp -s $interface_1_ip $interface_1_mac
sudo /usr/sbin/arp -s $interface_2_ip $interface_2_mac

# OS ignores packets on this interface -WHAT NOW? 
# first idea: try to forward it from the incoming interface to the loopback
# forwarding does not work - sniffing on lo shows no packets...
sudo /sbin/iptables -t nat -A PREROUTING --in-interface $interface_1 --destination $interface_1_ip -j DNAT --to-destination 127.0.0.1
sudo /sbin/iptables -t nat -A PREROUTING --in-interface $interface_2 --destination $interface_2_ip -j DNAT --to-destination 127.0.0.1


```

---

