---
title: "Network configuration issues"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by jjleonb on 2011-07-22
Hi, thanks in advance anyway...  Here are the facts:
I'm connecting via wireless (wlan0) to the internet and I'm using a dhcp server via wired connection (eth0). Both of them are using manual configuration on /etc/network/interfaces/, by the way I'm using GUI interface, but an ubuntu server, when I enable my eth0 connection, and restart networking, it loses my internet connection, but after I disable the eth0 connection, it just connect itself right away, without restarting the service, I need to enable my wired connection 'cause I've said, I'm using this one to make the dhcp server, I don't know if it is a conflict between the the network manager applet (gui interface) and my manual configuration in /etc/network/interfaces. Here is the manual configuration
/etc/network/interfaces:
# The primary network interface
iface eth0 inet static
        address 192.168.1.16
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

iface wlan0 inet static
        address 192.168.1.15
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

here is my dhcp3-server configuration
 ddns-update-style none;
        default-lease-time 600;
        max-lease-time 7200;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.1;
        option domain-name-servers 200.42.213.11, 200.42.213.21;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.20 192.168.1.30;
        }

log-facility local7;

this is my configuration in the /etc/default/dhcp3-server
INTERFACES="eth0"

Any help would be very appreciated.

---

### Post by revinkey on 2011-07-22
hello jjleonb. i would love to help you out, however i am a little confused on what your dhcp-server is running on. please clarify.

---

### Post by e79 on 2011-07-22
If I understood correctly :

Wireless Router --> wlan0 on Ubuntu server (internet connection)  |  eth0 on Ubuntu server (for LAN and DHCP)   --> LAN 

If that's the case, you should try to remove the GATEWAY on your eth0, because (again, if I understood correctly) if you want your Ubuntu server to act as a router/gateway/dhcp for your LAN, you should only have 1 DEFAULT GATEWAY set on it (on WLAN0 that is). I hope I make sense for you.

---

### Post by Iowan on 2011-07-22
By definition (don't ask me to quote the source... spanning tree protocol???) a machine should only have one interface in a particular subnet. Having multiple gateways doesn't help either...;)

---

### Post by jjleonb on 2011-07-25
0.K.!!! I'm connecting wireless to the router that provides me the Internet service, and I have two machines connected to a little switch that I want in fact that connect to the internet and connect each other, as in a workgroup, and share files, share a printer (which is connected to my ubuntu server), they're both PC's with Windows XP, with my lan (eth0) connection. This is the reason I'm using the two network connections, as I have said I'm using my LAN connection as the interface that provides the pool of addresses.

---

### Post by e79 on 2011-07-25
I still beleive you don't need 2 NIC (Network Interface Card) here, and your server don't need to act as a router. I would personally do the following :

1. Deactivate the wireless on your Ubuntu server, leaving only 1 NIC; the eth0 (LAN) and connect it to your switch.

2. Connect all other machine/devices to this same switch (even the router).

3. Deactivate the DHCP on your Router since the Ubuntu server will do that job.

So basically all machines/devices on your network would be connected to the same switch, the DHCP service would be provided by your Ubuntu server, and your Default Gateway should be your router.

Just my $0.02

---

### Post by jjleonb on 2011-07-25
I think I didn't explain well my issue.  I have to use my wireless connection because the router is so far away where I have my PC's, that's the way I have to connect it (first floor router, PC's Third Floor), and the problem here is not with my wireless connection, as I said when I turn on my wired connection, my internet connection has conflicts. Here is a tip, I use my wired connection through the cli (/etc/network/interfaces), and my wireless connection through the network manager applet (GUI), What do you think: could be an issue?

---

### Post by jjleonb on 2011-07-25
0.K. part of the problem has resolved (thanks Iowan), apparently only one interface must be in one subnet.  Now I'm using a dhcp3 server in order to assign the IP Addresses to several PC's that are running Windows XP, and this is the configuration that I have in this moment in my /etc/dhcp3/dhcpd.conf

ddns-update-style none;
        default-lease-time 600;
        max-lease-time 7200;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.15;
        option domain-name-servers 200.42.213.11, 200.42.213.21;

#option definitions common to all supported networks...
#option domain-name-servers ns1.example.org, ns2.example.org;

subnet 192.168.1.192 netmask 255.255.255.192 {
        range 192.168.1.194 192.168.1.250;
        }
This is the configuration that I have in /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
        iface eth0 inet static
        address 192.168.1.193
        netmask 255.255.255.192
        network 192.168.1.192
        broadcast 192.168.1.255

And as I said before: the connection that I use for the internet is WLAN0 and is managed by Network Manager Applet (GUI), and it has a manual configuration with the IP Address 192.168.1.15, the router has the IP Address 192.168.1.1.  
The question is How do I connect the PC's that have windows XP to the internet using my ubuntu server.
From these PC's I can ping the router (in this case my wireless connection) 192.168.1.15, and the wired connection 192.168.1.193 which is the one that is directly connected.
Do I have to share a connection besides another configuration in my dhcp3 server.
Thanks in advance....

---

### Post by e79 on 2011-07-25
> **jjleonb said:**
> The question is How do I connect the PC's that have windows XP to the internet using my ubuntu server.
From these PC's I can ping the router (in this case my wireless connection) 192.168.1.15, and the wired connection 192.168.1.193 which is the one that is directly connected.
Do I have to share a connection besides another configuration in my dhcp3 server.
Thanks in advance....

Did you set your Ubuntu server as a router (since it needs to route packets between 2 different subnets now) following [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) ?
I think all you may be missing is this part (not sure though) :

> **Enable routing**

 
[LIST]
[*]Configure the gateway for routing between two interfaces by enabling IP forwarding:
[/LIST]

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" 

[LIST]
[*]Edit /etc/sysctl.conf and add these lines:
[/LIST]

net.ipv4.conf.default.forwarding=1 net.ipv4.conf.all.forwarding=1

---

### Post by jjleonb on 2011-08-02
Thanks a lot! I'm succesfully connecting to the internet through my wireless connection, and I'm using my another connection (Ethernet Connection) to distribute a DHCP Pool and Internet Connection too.  Thanks a lot...

---

### Post by e79 on 2011-08-06
I'm glad we could help you solve your issue !

and sorry for the late reply, I was away camping ;)

Cheers

---

