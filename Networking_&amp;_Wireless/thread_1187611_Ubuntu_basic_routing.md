---
title: "Ubuntu basic routing"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by wowiesy on 2009-06-14
Hi,

I'm new to setting up ubuntu (linux for that matter) and I intend to setup a router / firewall / vpn gateway at our business. To do this, I am setting up a test environment first at home, before I set it all up to run in our company. For the test environment, this is the setup

1. Linksys router (IP address: 192.168.1.1) - serves as Internet gateway

2. Ubuntu Server Box UBUNTUSERVER (eth0 address: 192.168.1.254) - static IP
                                 (eth1 address: 192.168.2.254) - static IP
              - eth0 connected to the Linksys router

3. Ubuntu Desktop UBUNTUDESKTOP (eth0 192.168.2.1) - static IP
          
4. Windows Desktop (dhcp configured, from the Linksys router) - at the time of my test last night, IP address: 192.168.1.102
 
            
for the Server box, /etc/network/interfaces is this: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.254
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0

auto eth1
iface eth0 inet static
address 192.168.2.254
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0

```from the Desktop Box, /etc/network/interface is this: 

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.0

```ip forwarding (through the /etc/sysctl.conf file has been set to 1 

iptables / ufw are all inactive at this stage.... 

where I am so far:
1. from UBUNTUSERVER, I can successfully ping 192.168.1.1, as well as 192.168.1.254 and 192.168.2.1 and  the Windows desktop

2. Initially, I couldn't ping the UBUNTUDESKTOP from the Windows client, I had to add a route to the Windows client like so:

```
route add 192.168.2.0 mask 255.255.255.0 192.168.1.254 metric 3

```for it to be able to ping the UBUNTUDESKTOP properly. pinging UBUNTUSERVER however was successful from the start. 

3. From UBUNTUDESKTOP, I can successfully ping both interfaces on UBUNTUSERVER; I can also successfully ping the Windows client, however I could not ping 192.168.1.1.  

This has kept me up all night last night.. 

My questions:

1. What am I missing here?  - I could ping 192.168.1.102 and 192.168.1.254, but I can't ping 192.168.1.1?  My understanding is, since these 3 clients are all on the same subnet, 192.168.1.1 should also be reachable.  I've read about proxy_arp... should I turn it on on the UBUNTUSERVER?  

2. I had to manually add the route statement in the windows desktop to be able to find the 192.168.2.0 network within my setup, is there a way for the Linksys router to set this up automatically through DHCP?

---

### Post by gombadi on 2009-06-14
> 
My questions:

1. What am I missing here? - I could ping 192.168.1.102 and 192.168.1.254, but I can't ping 192.168.1.1? My understanding is, since these 3 clients are all on the same subnet, 192.168.1.1 should also be reachable. I've read about proxy_arp... should I turn it on on the UBUNTUSERVER?

2. I had to manually add the route statement in the windows desktop to be able to find the 192.168.2.0 network within my setup, is there a way for the Linksys router to set this up automatically through DHCP?



You need to setup a route in the Linksys router so it knows to send packets for the 192.168.2.0/24 network via 192.168.1.254.

The ping packets from your Ubuntu Desktop will arrive at the router. When it replies it will look at its routes and see the 192.168.1.0/24 network is local but will not know about the 192.168.2.0/24 network so it will send the packets to its default gateway - i.e. the Internet.

Same fix for the Windows machine. It does not know about he 192.168.2.0/24 network so sends packets to the Linksys router which sends them to the Internet.

---

### Post by jonobr on 2009-06-14
Hello


Just a couple of comments/questions on the network design,
The windows box at 102, whats the purpose of this device?
Im thinking the ubuntu server may be acting as the firewall, so I would think the windows box should be behind the firewall and not between the two devices.

Im then guessing that this is leading to the problem for the windows box.

The windows box after it gets its ip information doesn't know where to send its unknown packets to only to the default gateway and devices on its own subnet.
If the packet it is sending is not on the local network, it will use its default gateway for doing that.

Without putting in the route to the second network its always going to send it packets to the default gateway.

The networking way out of this is to ensure any non smart routing device that doesnt process and route based on RIP or OSPF updates needs to send its information to a router to make its routing decision for it.
So, the network should be built to have end devices grouped into a lan or vlan  that are connected to the routing device (layer 3 router) which can perform the routing.
The windows box , given its in a bit of a no mans land at the moment, needs to have this additional information in there to help it route to the right network.


You can usually put a permanent route into the 1.1 to say any traffic for the 192.168.2.0 network should be routed through ubuntu server, however, you could start introducing routing loops there where it will try and send the packet back to the default gateway.
Therefore the most appropriate way to do this is to use an ICMP redirect message from the 1.1 device.
Basically when the windows box says I have got a packet for the .2 network,
 and I want .1 to handle this, .1 replies with an icmp redirect saying, the best way to router this is through 1.254

Its possible that this is whats going wrong on the ping to 1.1.
The only way to know for sure is to install wireshark on the 192.168.1.102 box and sniff the ping packets and see what happens to them

You will also need ( i reckon) the same trace on the desktop or ubuntu server, which ever is easier.

If you would like to setup those traces and do multiple ones and post them here we could look at them to see whats up.

You may run into another problem if you try to issue 
dchp address to the .2 network.
bootp requests are layer 2 and will not go through a router, and the response is the same.
You would typically (in cisco speak) need an ip helper statement to get through the router to allow a device supply IP addresses to the device on a different network.

Proxy and reverse arp , you mentioned, are ways for getting the mac address of a device not on the local network, so that is useful to keep in your back pocket.

---

### Post by wowiesy on 2009-06-15
> **gombadi said:**
> You need to setup a route in the Linksys router so it knows to send packets for the 192.168.2.0/24 network via 192.168.1.254. 

I should set this route in the LINKSYS router?  My UBUNTUSERVER has the following routes already:

```


192.168.1.0  255.255.255.0  eth0
192.168.2.0 255.255.255.0  eth1
gw 192.168.1.1  


```> 
The ping packets from your Ubuntu Desktop will arrive at the router. When it replies it will look at its routes and see the 192.168.1.0/24 network is local but will not know about the 192.168.2.0/24 network so it will send the packets to its default gateway - i.e. the Internet.


While I was testing this last night, traceroute wasn't yet installed so I wasn't able to know where it is passing to get through to 192.168.1.102...  I'll try to have it installed so that it could give me a better idea what's going on....  but from the configuration of UBUNTUSERVER (its routing table), the path to the 192.168.1.0/24 network should be to eth0...  since 192.168.1.1 is within the 192.168.1.0/24 network, then it should go through that route doesn't it?  What's going on behind the scenes here? 

In addition, from the UBUNTUDESKTOP, I was able to ping 192.168.1.102... I was assuming that it was able to do so through UBUNTUSERVER since the packets were first sent to 192.168.2.254 of UBUNTUSERVER, which routed the packet to its 192.168.1.254 interface, and then on to 192.168.1.102 (since they were already on the same subnet).. it didn't have to "pass through" the linksys router...  is this correct? 


> 
Same fix for the Windows machine. It does not know about he 192.168.2.0/24 network so sends packets to the Linksys router which sends them to the Internet.In my test, I added the route manually to the 2.0/24 network locally at the windows machine...  this manually added route enabled me to ping the 2.1 machine from the windows machine.    This solution above is another way of doing it (if I understand it properly)... what would happen then is the windows client (w/ default gateway 192.168.1.1) sends the packet to the gateway... the gateway, with a local routing table (2.0/24 network) mapped, it would know that the packet should be forwarded to 192.168.1.254 to get to the 2.0/24 network... is this what's happening behind?

---

### Post by jonobr on 2009-06-15
Hello

Just to reiterate, wireshark and/or tcpdump are tools used for this purpose to see whats happening and where the packets are going, if they were received and if not here they went and any messages associated.


This will give solid evidence and info

---

### Post by wowiesy on 2009-06-15
> **jonobr said:**
> Hello


Just a couple of comments/questions on the network design,
The windows box at 102, whats the purpose of this device?
Im thinking the ubuntu server may be acting as the firewall, so I would think the windows box should be behind the firewall and not between the two devices.

Im then guessing that this is leading to the problem for the windows box.




The windows machine was there only to test the routing being done by UBUNTUSERVER, as I understood it.   I wanted to test also my understanding of routing concepts. This will come in handy if I need to setup an ubuntu box that may route between 3 or more subnets (say 1 for the office LAN, another 1 for those accessing within the office through wifi, another 1 through the VPN link for those accessing outside of the office).  I wanted to test first the connectivity between the subnets, before iptables will come in to block of packets based on specific requirements. 

The windows machine somehow (as per my understanding) represents any machine in the 1.0/24 network... while the UBUNTUDESKTOP can represent any machine in the 2.0/24 network...   I can easily expand this to a lot more subnets (I guess the only limit to this would be the number of PCI slots I could find on the mboard of a machine ). 

My understanding of routing as of now is such:
1. Any client can easily get to a machine, as long as that machine is within the same subnet.
2. For addresses that are not in the same subnet, the packet goes to the gateway.
3. The function of a router is to route between subnets. If a subnet is known through its local routing table, then the kernel does the routing automatically. Only if the destination is not known or not mapped in the local routing table will the packet be sent by the router to its defined default gateway. It would be up to the gateway to resolve the path.  

Based on my understanding, and from my setup above, since UBUNTUSERVER already knows of the 1.0/24 and the 2.0/24 network in its routing table, why can't it route directly to 1.1 on the 1.0/24 network? Am I understanding the concept properly?

---

### Post by wowiesy on 2009-06-15
> **jonobr said:**
> Hello

Just to reiterate, wireshark and/or tcpdump are tools used for this purpose to see whats happening and where the packets are going, if they were received and if not here they went and any messages associated.


This will give solid evidence and info

wireshark / tcpdump should be installed on the UBUNTUSERVER or UBUNTUDESKTOP here?

---

### Post by jonobr on 2009-06-15
Hello


I would recommend that if your working on learning routing and how things are processed, put wirehsark on both and you will see how each deivce process the message.

On the Ubuntu server you have two ethernet cards so the trace may get complicated, I would recommend running two seperate traces on each interface,
imagine you have eth0 and eth1

you could run sudo tcpdump -w eth0.pcap -i eth0

and then a second one on 
sudo tcpdump -w eth1.pcap -i eth1

The -w option creates a trace file which can be opened with wireshark.

If you want to see everything in one trace file you can 
sudo tcpdump -w eth1.pcap -i any

However, as said, you may see a lot of traffic with the two interfaces defined,

What you should watch for are ICMP messages going from host to host and replies.

Wireshark is free and available in synaptic.....

---

### Post by jonobr on 2009-06-15
Hello


I should have also commented on the question you ask regarding your understanding.

I think in essence your explanation is correct.

The way it works is that, routing tables in devices which have them and build them, that is routers,
make a decision on each packet and where to send them,

Pretty much, a router (in this case its your ubuntu server and your 1.1 device,)  will receive a packet and look at its routing table and say, yep, I know this is intended for this network, out of this interface.
I.e. i have to send it to the 2.x network,  and ubuntuserver knows where that is.
or, I dont know where this packet is intended for, so I will send it to the the default route and let the next router decide what to do with it.
This packet will go from router to router for 16 hops using the RIP protocol, before the packet is considered dead.

Information is exchanged between gateways using a routing protocol, there are two popular ones for lans, RIPv2 and OSPF.
You network is probably using RIP.

What happens is each routing device sends a RIP update to let each other know the subnets its aware of.
Thats how all the routing tables get updated.

The way the devices know which network is what is that the subnet mask will define which portion of the IP addres is host and which is network.

For example if a packet is destined for 192.168.2.210
and has a subnet mask of 255.255.255.0 (which translates to 111111111 111111111 11111111 00000000)
The routing device knows the network is 192.168.2 and the device on that network is 210

So if you had setup these two networks with a class b subnet 
255.255.0.0 then the router would consider this network as the 192.168 network and the .1 and .2 designation would not be look at and would be considered the host portion.


The windows box doesnt have the intelligence of the router (it can) 
but needs to have a route inserted into it to say , there is a network here (in this case the .2 network) if it has a packet that is not for the .1 network, or the .2 network, it will use the default gateway, in this case, 
.1 to move and route its packets.

As mentioned, you can resolve this by telling the .1 gateway about the other network, or as I mentioned using an ICMP redirect message for that host or any hows on that network.

Hope this was of some use

---

### Post by jonobr on 2009-06-15
One other thing I forgto, if running tcpdump with the -w option,

you should use the -s switch and have it set to 1600

if you dont do that it will capture packets up to 64 bytes ( if i recall rightly)
and then display the [packets as truncated in wireshark.

---

### Post by wowiesy on 2009-06-15
I got it to work.

I put an entry in the linksys router (192.168.1.1) so it will know about the 2.0/24 network (which is through 192.168.1.254)...  

I'm still trying to learn how to use tcpdump (reading through the man page) but I think this is what went on:

1. From UBUNTUDESKTOP (192.168.2.1), the ping to 192.168.1.1 went to UBUNTUSERVER eth1 (192.168.2.254), then its eth0 (192.168.1.254) and then on to 192.168.1.1 (which is the linksys router).

2. However, since the linksys router ddn't know where to send the reply to 2.0/24, it got lost.  That may be the reason why when I did a ping on 192.168.1.1 from 192.168.2.1, the program seemed to hang.  It didn't put out any message like host unreachable or something...  it may be an indication that it has found 192.168.1.1, but it is still waiting for the reply, and since the linksys router couldn't reply (it didn't know how and where to send the reply), 2.1 was still waiting on the reply.

I will try to remove the routing entry in the linksys router later when I have learned to use tcpdump and wireshark...  and see what happens...

---

### Post by jonobr on 2009-06-17
Hello


Glad you got it working, although I still think the icmp redirect would be the best way??

Im thinking as your network grows you may encounter routing loops,

for example

a knows to get to c through b

b knows that a knows how to get to c and also knows itself how to get to C.

If the connection to c gets messed up b will know its link is down and will say, hang on, A knows a route to C.

However, As route is through B and sends the packet back to B who does not know how to use it.

This is a common problem encountered as networks grow,
This is resolved using something called split horizon with poison reverse,
split horizon is the solution for resolving routing loops using a technique called poson reverse.
It says that routing information cannot be sent over a link that a packet was received.
effectively "poisoning the route". Anyway,
On the tcpdump/wireshark side of things, these are just tools to help you understand whats going on.

They are going to be particularly useful for figuring out where packets are going and hardening your firewall/

If you have any questions, Ill be watching for those tcpdump/wireshark questions:-)

---

