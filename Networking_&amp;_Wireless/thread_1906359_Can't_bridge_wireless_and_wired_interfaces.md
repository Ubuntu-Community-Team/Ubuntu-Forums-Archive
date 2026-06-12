---
title: "Can't bridge wireless and wired interfaces"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by MidnightJava on 2012-01-08
I have a wired and wireless interface on my system, and I'd like to bridge them. I need broadcast packets to pass between the interfaces, because I need a system on the ra0 interface to be able to discover an Ethernet controller on the eth0 interface. After much reading online, it seems that what i need to do is create a bridge between the wired and wireless interfaces. But when I do that, the wireless interface gets disconnected, and reconnecting it is not successful. When I delete the bridge, the wireless interface connects almost immediately.

Here is my network configuration:

```
eth0      Link encap:Ethernet  HWaddr d4:85:64:9f:06:9e 
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::d685:64ff:fe9f:69e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68682060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32981721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:73761967812 (73.7 GB)  TX bytes:35411582728 (35.4 GB)
          Interrupt:42

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146073100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146073100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:141196736823 (141.1 GB)  TX bytes:141196736823 (141.1 GB)

ra0       Link encap:Ethernet  HWaddr 68:7f:74:7d:06:69 
          inet addr:192.168.1.224  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6a7f:74ff:fe7d:669/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1652713 errors:27 dropped:1 overruns:0 frame:0
          TX packets:707681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:284969278 (284.9 MB)  TX bytes:931799232 (931.7 MB)
  
```To add the bridge I do

```

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 ra0

```Here is my routing table

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 ra0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra0


```

---

### Post by jonobr on 2012-01-09
Hello


For your interfaces, your need to setup routing between the interfaces.

The difference between bridging and routing are that with bridging, this connects two interfaces that are on the same subnet,
that is , both of them are on the eg 192.168.1.x network, or the 192.168.2.x network.

If you have interfaces that are on two different interfaces, then then you will have to route between the two networks.

When a device on one network (ra0) needs to contact something on the eth0 network, the device needs to know to send the traffic to ra0 for eth0 and the machine knows how to route between the two,

what your doing will change your approach, so if you want to route between interfaces [here]("https://help.ubuntu.com/community/Router") is a detailed guide

Also, you could consider using ICS if you want to share the eth0 connection to your lan devices

---

### Post by MidnightJava on 2012-01-09
Thanks for your reply. I'm familiar with the difference between routing and bridging. I think I have established routing between the two devices by adding entries to the route table. I didn't post those commands, but I did post my routing table. I believe I'm routing, because I can ping from a system on the 192.168.1.0 subnet to address 192.168.2.2, which is the link partner to the eth0 interface. If I'm still missing something wrt routing, please let me know.

The problem I'm trying to solve is that I need broadcast frames to pass from ra0 to eth0 and back in the other direction. The reason for this is that a system on the 192.168.1.0 subnet is sending out discovery packets within broadcast frames, and the link partner to the eth0 interface is  configured to respond to those discovery packets.

 A router of course does not pass broadcast traffic. It's my understanding that by bridging eth0 and ra0, I establish layer two connectivity between each interface, including all broadcast frames. Is it problematic that I have a different subnet on each interface of the bridge? I think I tried giving eth0 an address on the same subnet as ra0, but maybe I had something else wrong at that time. Or is it OK to bridge between subnets?

---

### Post by jonobr on 2012-01-09
Hello


I misunderstood, apologies for that.

I understand better now what your trying to do, 
I have come up against this before (not with Ubuntu) but where a device needed to get bootp to a dhcp server on a different subnet.

This required the router to have a helper statement to pass specific traffic from that mac address to the other device and back again which would normally be blocked

You would not want that to happen whole sale.
You are also right, the router will stop all of these mac address going over to the other subnets without this statement.

What will normally happen is that the router will receive the packet and rebuild it for the other subnet and use its own mac as the source for the other device to respond to.

Im thinking you need iptables for this

I found [this link]("http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html")

which I thnk describes what you need.

> You can also use FORWARD chain:

 
/sbin/iptables -A FORWARD -i ethX -m mac --mac-source YOUR-MAC-ADDRESS-HERE -j ACCEPT
 

You can also use NEW and other supported states as follows so that a known MAC address can be forwarded:

 
/sbin/iptables -A FORWARD -m state --state NEW -m mac --mac-source YOUR-MAC-ADDRESS-HERE -j ACCEPT
 


---

### Post by MidnightJava on 2012-01-10
Thanks for the suggestion. So far it's not working, however. I entered rules for FORWARD and INPUT chains, as well as the NEW state. For example, I created an accept rule for ra0, specifying the MAC address of the system that would be sending broadcast frames on that interface.

The discovery protocol I'm working with sends UDP packets with dst port 1024, inside Layer 2 broadcast frames. With Wireshark on the Ubuntu system, I see these frames coming in on ra0, with capture filter 'broadcast and dst port 1024'. But they're not making it to the eth0 interface. When I capture on that interface with the same capture filter, I see no data. I also tried a capture filter on eth0 of just 'dst port 1024' in case the router was passing the UDP packets in some other sort of Layer 2 frame, but there is no data with this filter either.

Any idea what may be wrong? Do I need to do something to activate the iptables entries? I did try a reboot, and it's still not working. I don't know if the entries I made persist across reboots, so I entered them again after rebooting.

---

### Post by jonobr on 2012-01-10
Hey there

Im sure if it made through it would show on a tcpdump -i eth0 command,

I am wondering though if its is putting something out that your filter is not catching.

Maybe if you could run a generic wireshark , no filters and view the traffic to see if there is anything that may resemble that UDP traffic getting through the router.

You could also enable logging to see whats being dropped.
From the iptables howto [here]("https://help.ubuntu.com/community/IptablesHowTo")

```
sudo iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
```

This should produce output in /var/log/messages

lastly could you port your iptables -L 

Im know IP tables expert but maybe we could take a looksee

---

### Post by MidnightJava on 2012-01-10
So here is my iptables dump

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            MAC E0:F8:47:02:51:54 
ACCEPT     all  --  anywhere             anywhere            MAC D4:85:64:9F:06:9E 
ACCEPT     all  --  anywhere             anywhere            state NEW MAC E0:F8:47:02:51:54 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```With wireshark on eth0 with no filters I see no traffic, just some standard DNS queries and ICMP packets when I ping the interface.

I wonder if the iptables entries actually imply forwarding of broadcast traffic. It seems like it's just a way to do link Level-aware IP filtering. I think the missing piece is a bridge implementation. As I mentioned in my original post, adding a bridge between eth0 and ra0 just brings the links down. Maybe I'm not doing it right, but after I add a bridge I have to reboot the machine to get any IP connectivity to work, even after deleting the bridge.

How about the fact that my interfaces are configured with the network manager GUI tool that comes with Ubuntu? Maybe in order for bridging to work, I need to configure them in /etc/network/interfaces.

Unless someone has a promising idea, I'm ready to give up on having Ubuntu do this, and implement a hardware solution. A colleague offered to give me a wireless router that I can install as a client of my existing wireless router, and connect the Ubuntu system and other device to it in bridge mode. He says he used it in exactly the configuration I'm trying to set up. Probably there's a way to do this with Ubuntu, but I'm not hopeful I'm going to find the right incantation.

---

