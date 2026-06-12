---
title: "Two NICs"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by nytwolf on 2006-04-20
I'm having serious difficult trying to get two NICs working at the same time. I've had many different theories as to why, but all have failed miserably.

Before I post a bunch of data about what steps I go through for troubleshooting and configurations, I'd just like to ask if there are any obvious things that pertain specifically to having more than one NIC I could be overlooking.

I've tried both DHCP and statically assigned (would like to have static). Sometimes both NICs downright don't work, sometimes one works and the other doesn't, and on very rare occasions do they both work but that usually changes with one reboot.

I'll post configuration information later if it's needed.

Also, thanks to mii-tool, I do know they /always/ establish 100/Full and make an OK connection with my D-Link router/switch.

---

### Post by nytwolf on 2006-04-21
Here is the information I retrieved (thanks to another post):


```
root@beowolf:~# ifconfig eth0
eth0	Link encap:Ethernet  HWaddr 00:50:DA:15:C4:AF
	inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b)  TX bytes:1080 (1.0 KiB)
	Interrupt:10 Base address:0x1080
```

```
root@beowolf:~# ifconfig eth1
eth1	Link encap:Ethernet  HWaddr 00:40:F4:E8:F5:CF
	inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:33 errors:0 dropped:0 overruns:0 frame:0
	TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:2173 (2.1 KiB)  TX bytes:308 (308.0 b)
	Interrupt:10 Base address:0x1080
```

```
root@beowolf:~# lspci | grep Eth
0000:00:0e.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
root@beowolf:~# route -n
Kernel IP routing table
Destination	Gateway		Genmask		Flags	Metric	Ref	Use	Iface
192.168.0.0	0.0.0.0		255.255.255.0	U	0	0	0	eth0
192.168.0.0	0.0.0.0		255.255.255.0	U	0	0	0	eth1
0.0.0.0		192.168.0.1	0.0.0.0		UG	0	0	0	eth1
0.0.0.0		192.168.0.1	0.0.0.0		UG	0	0	0	eth0
```

```
root@beowolf:~# cat /etc/resolv.conf
domain myweji.com
nameserver 12.241.16.34
nameserver 12.241.16.35
```

```
root@beowolf:~# cat /etc/network/interfaces
# Removed comments for this forum post, also commented out the following:
#mapping hotplug
#	script grep
#	map eth0
# Begin file:

auto lo eth0 eth1
iface lo inet loopback

iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 12.241.16.34 12.241.16.35

iface eth1 inet static
	address 192.168.0.3
	netmask 255.255.255.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 12.241.16.34 12.241.16.35
```

```
C:\>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : canisrufus
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : myweji.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : myweji.com
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-40-CA-2B-4F-47
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.10
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Wednesday, April 19, 2006 11:13:42 PM
        Lease Expires . . . . . . . . . . : Wednesday, April 26, 2006 11:13:42 PM

```

---

### Post by mips on 2006-04-22
Your problem is a simple one. You have both nics on one machine within the same subnet, this is a big no-no.

See post #11 below for a explanation.
[http://www.ubuntuforums.org/showthread.php?t=117356](http://www.ubuntuforums.org/showthread.php?t=117356)

If you want both (or more) nics on one machine to work at the same time you HAVE to do nic bonding or put each nic into a different subnet. In your case I suggest nic bonding.

Solution is here:
[http://www.ubuntuforums.org/showthread.php?t=99668](http://www.ubuntuforums.org/showthread.php?t=99668)

---

### Post by nytwolf on 2006-05-07
Thank you very much for your input. I had no idea about that rule, I may have learned about it in Cisco training a long, long time ago but since forgotten it.

My overall goal is to have to IP addresses on the machine and recently I was just reading documentation from several sources and ran across virtual interfaces. Within an hour I got it setup with two ip addresses.

Thanks again for your suggestion, however. Still in the learning phase I like to get as much input as possible.

---

### Post by mips on 2006-05-07
[QUOTE=nytwolf]Thank you very much for your input. I had no idea about that rule, I may have learned about it in Cisco training a long, long time ago but since forgotten it.
[/QUOTE]

Yes, they definately tought you that from the very beginning in the CCNA training ;)

---

### Post by j3cakes on 2006-11-22
I'm trying to do the same thing but I don't understand why it can't be done this way...

The two examples given in post #11 of that link aren't strictly relevant (or accurate.)

Example 1
A device with two interfaces is only called an 'IP Router' if it's 'forwarding' packets between the two.

" The process of sending an IP packet out onto another network is called "forwarding" an IP packet.  A computer that has been dedicated to the task of forwarding IP packets is called an "IP-router"." ([http://www.ietf.org/rfc/rfc1180.txt](http://www.ietf.org/rfc/rfc1180.txt) (section 2.4))

but I'm not trying to forward packets I just want to have one NIC as a virtual server for azureus and the other for access/mgmt.

Example 2 discusses the broadcast of ICMP messages when a box receives an ip packet with an address from a different subnet, which doesn't apply in this case because I'm trying to get them on the same subnet.

By the way, the reason it's covered in the CCNA is because Cisco routers ARE IP routers and you can't configure more than one interface on the same router to the same subnet.

---

### Post by mips on 2006-11-23
Configure your interfaces as per your above example, in the same network and post the following outputs here:

ifconfig -a
route -n

After that I will try to provide you with an answer. I see where you are coming from though.

---

### Post by mips on 2006-11-23
> **j3cakes said:**
> 
By the way, the reason it's covered in the CCNA is because Cisco routers ARE IP routers and you can't configure more than one interface on the same router to the same subnet.

But you can disable routing on any cisco router simply by issuing the  "no router ospf xxx" command, routing is not enabled by default at all. You can bridge interfaces with no routing running as well. Yet, even with routing disabled you cannot place two interfaces in the same network/subnetwork.

---

### Post by j3cakes on 2006-11-23
In the end I've decided to go with creating a separate vlan for azureus (for QoS) so I don't need to sort out having two NICs on the same network. I think the problem I had was that it mucked up the routing when I added the second NIC. 

but, umm,.. actually the cisco IOS command is 'no ip routing': a router will still route without a dynamic routing protocol like ospf (using statics and directly-connected networks.) Routing is enabled by default on routers (and route processor modules like MSFCs) but not on switches.

Bridging works at Layer 2 so there are no ip addresses.

You're right about assigning IPs from the same subnet onto different interfaces. It simply won't let you do it.

---

### Post by mips on 2006-11-24
> **j3cakes said:**
> In the end I've decided to go with creating a separate vlan for azureus (for QoS) so I don't need to sort out having two NICs on the same network. I think the problem I had was that it mucked up the routing when I added the second NIC. 

but, umm,.. actually the cisco IOS command is 'no ip routing'


But I thought you said that you are not using routing ? That will muck up routing as you now have two interfaces via which you can get to one designated network.

Oops, I forgot about the no ip routing command, bit rusty.

---

### Post by j3cakes on 2006-11-24
I haven't got round to doing it yet but I'm hoping I can configure my crappy netgear adsl router with a dmz (or a vlan or something similar.) At the moment I'm just using the single NIC.

actually, it might not be that hard to sort out the ubuntu box to do it all..

how do I configure a static route in ubuntu? I tried 'route add' but it failed telling me that the 'correct' usage was 'inet_route add' which I tried and it said 'no such command.'

so let's say: my lan is 10.10.0.0/24; the router is 10.10.0.254l; eth0 is 10.10.0.95; and eth1 is 10.10.0.96.

I'd like packets destined for:
-10.10.0.0/24 to go out eth1.
-all other destination addresses (ie the def route) to go out eth0.

can you please help me with the commands to sort that out? is it even possible or will ubuntu automatically recognise 10.10.0.0/24 as being 'directly-connected' and send packets out that interface anyway?

I don't want the ubuntu box to act as a router (taking an ip packet from one interface and forwarding out another) but I'm guessing I have to configure it to know which of its interfaces it should send certain packets. So it won't be a 'router' but it will route.

---

### Post by mips on 2006-11-24
> *is it even possible or will ubuntu automatically recognise 10.10.0.0/24 as being 'directly-connected' and send packets out that interface anyway?*

Yes, this usually happens by default & if you specify a gateway a default route usually also gets added i would say from previous experience.
[FONT=Arial][SIZE=3]
There are two ways.

route add & ip route add (you have to- **sudo aptitude install iproute**)

Static Route:
[/SIZE][/FONT]```
sudo ip route add 10.10.0.0/24 via 10.10.0.96 dev eth1
* or*
sudo route add -net 10.10.0.0 netmask 255.255.255.0 gw 10.10.0.96  dev eth1
```

Default Route:
```
sudo route add default gw 10.10.0.254 dev eth0
```

These will only be temporary until you reboot.
Edit your /etc/network/interfaces and add the following lines after the under the respective interfaces:
[FONT=Arial][SIZE=3]
Static Route:
[/SIZE][/FONT]```
up ip route add 10.10.0.0/24 via 10.10.0.96 dev eth1
* or*
up route add -net 10.10.0.0 netmask 255.255.255.0 gw 10.10.0.96  dev eth1
```

Default Route:
```
up route add default gw 10.10.0.254 dev eth0
```
Instead of **up **you can also try **post-up**.

If you want to delete a route:
```
sudo route del -net 10.10.0.0 netmask 255.255.255.0 gw 10.10.0.96  dev eth1
```[COLOR=Red]

I dunno if the above is going to work for you though[/COLOR], linux is probably going to add a route for the directly connected networks when it starts up. You will have delete that route when the inteface comes up.

You will also have to disable IP forwarding if it is not already disabled.
```
sudo echo 0 > /proc/sys/net/ipv4/ip_forward  # 1=enable 0=disable
```
But this might disable all routing.

Let me know how it goes, should be interesting. Should actually duplicate your setup and try it myself but somehow I suspect it wont work.

---

### Post by j3cakes on 2006-11-24
ok thanks for that. I'll give it a go and let you know what happens.

---

### Post by mchan on 2007-03-31
Hi, 
I am enountered similar issue but with a twist.
I have one intergated NIC LAN (eth0) IP DHCP client assigned by 192.168.1.x network router connected to internet, and 2nd PCI NIC (eth1) is set up as DHCP for 192.168.2.x subnet.
eth0 have no problem to Internet
eth1 have no problem in assigning LAN IP address to DHCP cleients
eth1 cannot gain access to Internet 

Do I need to have "IP Route" need to enable?
Do I need to have "IP Forward" enable?
Are these both are same?
Do I need to use "bridging" and where do I get the package for installation?

(Actual IP Address assigned by ISP)
142.179.103.xx
255.255.248.0
DNS1:154.11.128.59
DNS2: 154.11.128.187

(LAN)
Router IP: 192.168.1.1
Subnet Mask: 255.255.255.0
DHCP Address range: 192.168.1.100-192.168.1.200

eth0: dhcp
subnet: 255.255.255.0 
GW: 192.168.1.1
DNS: ISP DNS   


# Want to use NIC eth1 to act as DHCP server to assign the following LAN IP address
Subnet IP range: 192.168.2.100 192.168.2. 200
Subnet Mask: 255.255.255.0
GW: 192.168.2.1
# What DNS gateway that I need to put into this eth1 ?
DNS: ??????
eth1 (static? 192.168.1.11)

Any help will be greatly appricated.
Michael

---

### Post by mips on 2007-03-31
Michael,

Try Firestarter. Read it&#347; manual on the website, very easy to follow. You might have to enable a dhcp server as well.

The harder way:
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

You will just have less interfaces.

---

### Post by BlueNoteExpress on 2008-01-04
I have a similar question.  Maybe someone can help me with the setup.

I have a Linux machine that I want to use as a network filter.  This linux machine has 2 network cards and will run an application that will decide which packets get sent on and which get dropped.  Let's say that the network cards are configured like this:

eth0:  10.10.0.230
eth1:  10.10.0.231

I want information to come in on eth0 and run through the filter program and then go back out on eth1 if the filter approves it.  Likewise, I want information to flow from eth1 to eth0.

Does anyone know how I could set this up?  Right now, I only have access to this machine from one end of the network, and it can ping both of the Linux machine's IPs.  The other end of the network can't ping either IP.

Any assistance getting this working is greatly appreciated.

---

### Post by mips on 2008-01-05
See Post#3

---

### Post by BlueNoteExpress on 2008-01-07
> **mips said:**
> See Post#3

I don't really think NIC bonding is what I want to do, and due to the network architecture, I'd really like to avoid putting each NIC into its own subnet.  I could probably do that as a last resort, but I'd really, really like to avoid doing so if at all possible.

I guess what I want to do is use this PC as a router of sorts.  Instead of traditional router software, it will be running another application though.  Is it possible to do something like this using a Linux machine with 2 NICs in the same subnet?

I really only know enough about networking to be dangerous so the simpler the explanation, the better.

Thanks.

---

### Post by mips on 2008-01-08
> **BlueNoteExpress said:**
> 

I guess what I want to do is use this PC as a router of sorts.  Instead of traditional router software, it will be running another application though.  Is it possible to do something like this using a Linux machine with 2 NICs in the same subnet?

I really only know enough about networking to be dangerous so the simpler the explanation, the better.


You basically want to turn your PC into a router. A router cannot have the same network on two seperate interfaces, it's not going to work. If you want to turn your pc into a router use two different networks.

I don't know if you would be able to stay in the same network and have iptables filter stuff. I would suggest reading the iptables documentation. This is not one of my strong points to be honest.

---

