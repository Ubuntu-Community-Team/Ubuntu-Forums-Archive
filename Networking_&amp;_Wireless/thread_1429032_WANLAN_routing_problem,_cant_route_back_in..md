---
title: "WAN/LAN routing problem, cant route back in."
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by RyanRahl on 2010-03-13
Hi, I've got an Ubuntu web server running 9.04 & Apache2. Ive got 2 NICs, one with an internal address for the LAN and one with and external address for the WAN to host the websites. My IP configuration is as follows (/etc/network/interfaces):

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface (WAN)
iface eth0 inet static
	address 63.231.18.xxx
	netmask 255.255.255.xxx
	broadcast 63.231.18.xxx
	network 63.231.18.xxx
	gateway 63.231.18.xxx

# The secondary network interface (LAN)
iface eth1 inet static
	address 192.168.200.xxx
	netmask 255.255.255.x
	broadcast 192.168.200.xxx
	network 192.168.200.x
	gateway 192.168.200.x

Now, i can access the internal address just fine from all the LAN nodes but i can not reach the external address. I found this out while trying to access our website from the LAN. I have two DNS entries that that point to the WAN IP and while on the LAN it won't connect but everyone outside the LAN connects just fine (my phone, other internet connected computers, etc). This is my routing table:

> netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
63.231.18.xxx   0.0.0.0         255.255.255.xxx U         0 0          0 eth0
192.168.200.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         63.231.18.xxx   0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.200.x   0.0.0.0         UG        0 0          0 eth1

When i do a traceroute from a LAN PC and it makes it all the way to the router and then just stops. I'm probably missing something very simple, its been probably 10 years since i took a class in this.

---

### Post by Iowan on 2010-03-14
The second default gateway may be causing problems. Remove (comment out) the gateway line on eth1, save, and restart.

---

### Post by l4zy on 2010-03-15
# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface (WAN)
iface eth0 inet static
address 63.231.18.xxx
netmask 255.255.255.xxx
broadcast 63.231.18.xxx
network 63.231.18.xxx
gateway 63.231.18.xxx

# The secondary network interface (LAN)
iface eth1 inet static
address 192.168.200.xxx
netmask 255.255.255.x
broadcast 192.168.200.xxx
network 192.168.200.x 
gateway 192.168.200.x <-- Change this one to your eth0 ip-address 63.231.18.xxx. 

If you want to get outside of your LAN, you need to set proper gateway address. Which is in this care you eth0 external address.

---

### Post by RyanRahl on 2010-03-15
I tried both changing the gateway and commenting out the gateway on eth1. Neither of which made a difference. Maybe I'm not explaining properly.

[I]"If you want to get outside of your LAN, you need to set proper gateway address. Which is in this care you eth0 external address."

[/I]The server can get outside the lan just fine from both IP's. I am running a gateway with an internal IP and external as well (63.231.18.xxx and 192.168.200.xxx). The problem is that any computer on the 192.168.200.x network has no problem connecting to the 192.168.200.xxx address on the server but will not connect to the 63.231.18.xxx address. 

This is only really a problem when the users in the office on the 192.168.200.x network want to access our website. Basically the user enters 'example.com' in their web browser and the browser attempts to connect to 63.231.18.xxx but it just times out (if the user simply enters 192.168.200.xxx the webpage comes right up). I'm not in the office right now so i can't give a traceroute output but i remember doing a traceroute from a LAN PC and it follows the route all the way to the gateway on eth0 and then just completely stops and times out. Hope this extra information helps. Any ideas would be greatly appreciated.

also i don't know if this is relevant but when i change the network config file and save it and to a network restart **[COLOR=Red]i get this output:[/COLOR]**

**> /etc/init.d/networking restart**
 * Reconfiguring network interfaces...
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
   ...done.

**[COLOR=Red]From this configuration:[/COLOR]**

# The primary network interface
iface eth0 inet static
    address 63.231.18.xxx
    netmask 255.255.255.xxx
    broadcast 63.231.18.xxx
    network 63.231.18.xxx
    gateway 63.231.18.xxx

# The secondary network interface
iface eth1 inet static
    address 192.168.200.xxx
    netmask 255.255.255.xxx
    broadcast 192.168.200.xxx
    network 192.168.200.xxx
    #gateway 63.231.18.xxx <----Commented out

[B][COLOR=Red]and this output:[/COLOR][COLOR=Red]
[/COLOR][/B] 
**> /etc/init.d/networking restart**
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
SIOCDELRT: No such process
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
SIOCADDRT: No such process
Failed to bring up eth1.
   ...done.

[COLOR=Red][B]From this configuration:

[/B][/COLOR]# The primary network interface
iface eth0 inet static
	address 63.231.18.xxx
	netmask 255.255.255.xxx
	broadcast 63.231.18.xxx
	network 63.231.18.xxx
	gateway 63.231.18.xxx

# The secondary network interface
iface eth1 inet static
	address 192.168.200.xxx
	netmask 255.255.255.xxx
	broadcast 192.168.200.xxx
	network 192.168.200.xxx
	gateway 63.231.18.xxx <---[I]eth0 IP address

[/I]it says *"Failed to bring up eth1" *but eth1 still responds to network requests without any problems.

---

### Post by helgman on 2010-03-15
Hello,

Make sure that you've got the basics (that the machine is actually routing) ...

```
cat /proc/sys/net/ipv4/ip_forward
``` 

should return 1.

Regards,
Helgman

---

### Post by RyanRahl on 2010-03-15
[B]Executed command:

> cat /proc/sys/net/ipv4/ip_forward[/B]

returned: "1"

---

### Post by helgman on 2010-03-15
I'm trying to replicate your problem but no luck ...

My Ubuntu Server acts as server and I can connect just fine.

Add a route to what would be your outside network, works fine.

Starts NAT via iptables just to rule out that option - works fine.

Just to clear something up for me - the clients on the LAN connects to the Internet via the router?

Also, can't route back in ... the router/gateway is the web server or is that a different machine?

Regards,
Helgman

---

### Post by Iowan on 2010-03-15
If I understand correctly - you want to route from an internal address to the external port? The router may not let you do that for security reasons (but I've been wrong before...).

---

### Post by RyanRahl on 2010-03-15
My apologies, i should have made this clear in the first post.
I am connected to the internet via an Actiontec M1000 DSL router and it serves as a router for the server and the lan clients. It has 2 IPs:

WAN IP: 63.231.18.xxx
LAN IP: 192.168.200.xxx

So the router and the server are two different devices.
Maybe i should just use the server as the router for the LAN?
I would need to disable NAT on the server right?

---

### Post by RyanRahl on 2010-03-16
OK. Problem solved. I am now using the server as the default gateway for all my LAN traffic. No more issues. I'm really great full for everyones help. This was my first post ever to ubuntuforums and it has inspired me to spend a lot more time here. TTYL.

---

### Post by FernandoTertiary on 2011-05-28
Hola,

What is the way wherein a person could configure such a network from the beginning? Am with necessity for the same configuration utilities, though the term was called "Loopback" within the OpenSim Grid circle.
The scenario is a Local Server operates with a Server Instance to connect to a External Server operating a Robust Instance. Each various Local Server Instance connect to the Robust Server to establish a Server Grid community.
The problems within the personal local network pertain the Local Server Instance not doing a "Handshake" with the Robust Server properly. The result is the Local Server Instance is displayed with the Robust Server Instance, though with limited interaction. In other words, within the particular scenario, the Sim Grid is online, though it can't be reached nor spoken to.
Am very grateful for your experience & expertise.

Gracias always.

---

