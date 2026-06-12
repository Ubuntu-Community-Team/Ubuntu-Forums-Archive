---
title: "shared internet connection two NICs"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by rjagla on 2010-04-18
I am setting up a shared ADSL network and have hit a wall. I have two machines, one Ubuntu 9.10 with two NICs eth0 and eth1 (my desktop, call it UBU) and a CentOS based server with eth0 (that will eventually be a cluster server, call it IBM). I want  UBU to share the DSL connection with the rest of the small network. The UBU machine is connected to a Motorola 2210-02-1022 through eth0 and to IBM through eth1. 

The following outputs are from UBU:
 /etc/network/interfaces:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1



# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1
'

When I restart the network I get this:

> bob@Pearl:~$ sudo /etc/init.d/networking restart
 * /etc/network/options still exists and it will be IGNORED! Read README.Debian of netbase.
 * Reconfiguring network interfaces...                                          
SIOCADDRT: No such process
Failed to bring up eth0.
SIOCADDRT: No such process
Failed to bring up eth1.The output of ifconfig is:
> 
bob@Pearl:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:f7:9a:bd  
          inet addr:192.168.1.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fef7:9abd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7137414 (7.1 MB)  TX bytes:2826842 (2.8 MB)
          Interrupt:28 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:05:5d:51:fa:f8  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe51:faf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1440 (1.4 KB)  TX bytes:17076 (17.0 KB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12074 (12.0 KB)  TX bytes:12074 (12.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xxx.160.177.199  P-t-P:xxx.160.177.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:14447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:6756200 (6.7 MB)  TX bytes:2389196 (2.3 MB)I have edited the iptables as described at the Ubuntu documentation:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

> **Configure NAT**

 Configure iptables for NAT translation so packets can be correctly routed through the Ubuntu gateway. 
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

(rule1 allows forwarded packets (initial ones), rule2 allows forwarding of established connection packets (and those related to ones that started), rule3 does the NAT.) 
 
**Enable routing**

 
[LIST]
[*]Configure the gateway for routing between two interfaces by enabling IP forwarding:
[/LIST]

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" 

[LIST]
[*]Edit /etc/sysctl.conf and add these lines:
[/LIST]

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

I am able to ping 192.168.1.1 from IBM (eth0 192.168.1.100) and am able to ping 192.168.1.100 from UBU (eth0 192.168.1.1) when I first startup UBU, but if I restart the network, it fails to ping either way. If I don't restart the network (after rebooting the system), I am able to ping the 192.168.x.x network but cannot get external responses.

I think that it may be an issue with the Network Manager, I did not use it to assign the addresses, but I did mess with it the past to try and setup the DSL, but reverted to using dsl-provider cmd tool manually because the ubuntu network manager sucks.

Any ideas?

---

### Post by Iowan on 2010-04-18
Having two interfaces in the same subnet will probably cause problems - as will having two gateways.

---

