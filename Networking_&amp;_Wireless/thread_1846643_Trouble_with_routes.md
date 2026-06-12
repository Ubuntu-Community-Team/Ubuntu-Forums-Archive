---
title: "Trouble with routes"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by RamonB84 on 2011-09-19
I'm experiencing some weird issues with a network configuration on an Ubuntu server and I was hoping someone here could perhaps enlighten me with some useful tips. I'm rather on the end of things I can think of to test at the moment :)
 
We're running several servers with 2 NIC's.
eth0 - 172.17.37.2/24
eth1 - 10.239.37.2/24
 
Eth0 should has the default gateway upstream. This is working fine. All traffic aimed for network 10.239.254.0/24 should be redirected to a route in the 10.239.37.0/24 network, namely 10.239.37.254. Thus I have added a route for this.
 
/etc/network/interfaces
> 
auto eth0
iface eth0 inet static
address 172.17.37.2
netmask 255.255.255.0
gateway 172.17.37.254
 
auto eth1
iface eth1 inet static
address 10.239.37.2
netmask 255.255.255.0

 
Output of netstat -rn
> 
Kernel IP routing table
Destination Gateway Genmask Flags MSS Windows irtt Iface
10.239.37.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
172.17.37.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
10.239.254.0 10.239.37.254 255.255.255.0 UG 0 0 0 eth1
0.0.0.0 172.17.37.254 0.0.0.0 UG 0 0 0 eth0

 
The following problem occurs:
I can ping any external address ( tested with 8.8.8.8 )
I can ping other servers in the 10.239.37.0/24 network, including the gateway.
I cannot ping any host in the 10.239.254.0/24 network.
 
When traceroute, it seems like the host does not even use the entry in the routing table. To me it looks like it is handling the entry like it is classful, so seeing the NIC as 10.0.0.0/8 and therefor logically not using the routing table.
 
Anybody got any ideas about what I can try next? When installing Windows instead in the exact same configuration, the issue does not occur. I've tried several live cd's (Debian and Knoppix with kernel 2.4) and they all show the same problem.
 
Thanks in advance for your time.

---

### Post by SeijiSensei on 2011-09-19
> **RamonB84 said:**
> The following problem occurs:
I can ping any external address ( tested with 8.8.8.8 )
I can ping other servers in the 10.239.37.0/24 network, including the gateway.
I cannot ping any host in the 10.239.254.0/24 network.

You don't have any routes to 10.239.254.0/24.  The route for 10.239.37.0 has a 255.255.255.0 netmask so it only handles traffic for the .37 subnet.  Thus traffic intended for 10.239.254.0/24 is sent out the default gateway.

If 10.239.37.254 is the gateway for all 10/8 networks, just add a static route like:

```
ip route add 10.0.0.0/8 via 10.239.37.254
```

---

### Post by RamonB84 on 2011-09-19
> **SeijiSensei said:**
> You don't have any routes to 10.239.254.0/24. The route for 10.239.37.0 has a 255.255.255.0 netmask so it only handles traffic for the .37 subnet. Thus traffic intended for 10.239.254.0/24 is sent out the default gateway.
 
If 10.239.37.254 is the gateway for all 10/8 networks, just add a static route like:
 
```
ip route add 10.0.0.0/8 via 10.239.37.254
```
 
At first, thanks for your reply.
 
I think I have a route to the 10.239.254.0/24 network, visible in the routing table as this entry:
10.239.254.0 10.239.37.254 255.255.255.0 UG 0 0 0 eth1
 
it has been added with the command
route add -net 10.239.254.0 netmask 255.255.255.0 gw 10.239.37.254
 
Am I overlooking something?

---

### Post by jonobr on 2011-09-19
interesting post,

Did you get to the bottom of this?

I think your right that its a fair assumption that it sees 10 and assumes class a.

Would adding broadcast help?

```
iface eth1 inet static
address 10.239.37.2
netmask 255.255.255.0 
broadcast 10.239.37.255
```



Seen anything interesting on wireshark or tcpdump?

---

### Post by SeijiSensei on 2011-09-19
> **RamonB84 said:**
> it has been added with the command
route add -net 10.239.254.0 netmask 255.255.255.0 gw 10.239.37.254
 
Am I overlooking something?

No, I missed it.

What kind of device is 10.239.37.254?  A traditional router or a Linux box?  If the latter, does it have IP forwarding enabled in its /etc/sysctl.conf?  Many Linux distributions, include Ubuntu, disable IP forwarding by default as a security measure.  There are instructions about how to enable it in sysctl.conf.

Does 10.239.37.254 have any kind of firewalling rules?  Are packets accepted from both sides and is forwarding permitted both ways?

Finally, do the machines in 10.239.254.0/24 have routes to 10.239.37.0/24?  The packets may be going to the machines in 10.239.254.0/24, but the return traffic may not be routed correctly.

---

### Post by RamonB84 on 2011-09-20
> **jonobr said:**
> interesting post,
 
Did you get to the bottom of this?
 
I think your right that its a fair assumption that it sees 10 and assumes class a.
 
Would adding broadcast help?
 
```
iface eth1 inet static
address 10.239.37.2
netmask 255.255.255.0 
broadcast 10.239.37.255
```
 
 
 
Seen anything interesting on wireshark or tcpdump?
 
Not quite yet sadly. However I did try TCP dumping, thanks for that tip. Because I have no network connectivity to the machines from my VLAN (due to this issue) I have added them as a screenshot.
 
The routing table:
[IMG]http://i51.tinypic.com/2r7nifn.png[/IMG]
 
TCPdump:
[IMG]http://i54.tinypic.com/281atfl.png[/IMG]
 
It really seems to think 10.239.254.0/24 is direct connected as far as I can make up from the dump. It does do an ARP request on the router IP but seems not to use it, or am I seeing this wrongly?
 
What is stranger to me, why is it running IGMP? Is this default behaviour?

---

### Post by RamonB84 on 2011-09-20
> **jonobr said:**
> interesting post,
 
Did you get to the bottom of this?
 
I think your right that its a fair assumption that it sees 10 and assumes class a.
 
Would adding broadcast help?
 
```
iface eth1 inet static
address 10.239.37.2
netmask 255.255.255.0 
broadcast 10.239.37.255
```
 
 
 
Seen anything interesting on wireshark or tcpdump?
 
With boardcast, results seem to be the same:
[IMG]http://i55.tinypic.com/f1cu80.png[/IMG]

---

### Post by RamonB84 on 2011-09-20
> **SeijiSensei said:**
> No, I missed it.
 
What kind of device is 10.239.37.254? A traditional router or a Linux box? If the latter, does it have IP forwarding enabled in its /etc/sysctl.conf? Many Linux distributions, include Ubuntu, disable IP forwarding by default as a security measure. There are instructions about how to enable it in sysctl.conf.
 
Does 10.239.37.254 have any kind of firewalling rules? Are packets accepted from both sides and is forwarding permitted both ways?
 
Finally, do the machines in 10.239.254.0/24 have routes to 10.239.37.0/24? The packets may be going to the machines in 10.239.254.0/24, but the return traffic may not be routed correctly.
 
10.239.37.254 is usually  a HSRP address offered by 4x Cisco 4506. However to exclude bad configurations on the network part, 10.239.37.254 is now offered as a plain VLAN interface. There are no ACL configured on the VLAN interface, nor on the 10.239.254.0/24 interfaces. Other machines from other VLANs have connectivity this way without issues. Also, when I install Windows instead of Linux on the server in question, it works.
 
I must be overlooking something but I don't know what. It seems unreasonable to think of this as a bug cause there would be many people already who already noticed this I think.

---

### Post by RamonB84 on 2011-09-20
> **RamonB84 said:**
> Not quite yet sadly. However I did try TCP dumping, thanks for that tip. Because I have no network connectivity to the machines from my VLAN (due to this issue) I have added them as a screenshot.
 
The routing table:
[IMG]http://i51.tinypic.com/2r7nifn.png[/IMG]
 
TCPdump:
[IMG]http://i54.tinypic.com/281atfl.png[/IMG]
 
It really seems to think 10.239.254.0/24 is direct connected as far as I can make up from the dump. It does do an ARP request on the router IP but seems not to use it, or am I seeing this wrongly?
 
What is stranger to me, why is it running IGMP? Is this default behaviour?
 
Just noticed. One ARP request, 2 replies? Definitly seems like there is an IP conflict of some kind. To be continued...
 
Maybe Windows just works because it does not handle the second reply as it should.

---

### Post by RamonB84 on 2011-09-20
Alright, problem solved! :)
 
2 ARP replies being visible in the tcpdump lead to the root cause of the problem.
 
IP address 10.239.37.254 was previously applied to an Cisco ASA firewall in the same subnet. This firewall's address was changed to 10.239.37.240 before configuring 254 on the HSRP VLAN interface on our core infrastructure. However, it still seemed to reply on ARP requests for 10.239.37.254.
 
Rebooted the firewall, cleared the ARP entry for 10.239.37.254 on the Linux server and it works again :p
 
Thanks for your replies guys. The tip to use tcpdump helped us solve this case.

---

### Post by jonobr on 2011-09-21
Sweet

Sorry Im only picking this up now, but Im glad you got it

Aint networking a pain in the neck when it doesn't work?

Thoroughly exhilarating when it does:-)

---

