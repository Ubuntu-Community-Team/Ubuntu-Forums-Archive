---
title: "2 NICs No pings on local network."
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by trubshac on 2008-12-19
Hi

Eventually, I am looking to install a transparent proxy (principally so that I can check that the kids have only visited reasonable websites).  For now, I'd be happy with a working system!  This is my setup:

    DSL ROUTER             
192.168.7.254 static ip - DHCP turned off

    SERVER
192.168.7.251 on eth0 to router
192.168.7.250 on eth1 to my lan

    PC1 on my lan
192.168.7.46 - DHCP client


The server is running Intrepid (Gnome not server) and is acting as a DHCP server to my LAN.  The server's IP addresses are static and are set by /etc/network/interfaces thus:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address	192.168.7.251
	netmask	255.255.255.0
	network 192.168.7.0
	broadcast 192.168.7.255
	gateway	192.168.7.254

auto eth1
iface eth1 inet static
	address 192.168.7.250
	netmask 255.255.255.0
	network 192.168.7.0
	broadcast 192.168.7.255


All internet functions on the server itself are fine.
PC1 on my lan is correctly getting it's IP address from my server - I have proved this by changing the IP allocation in /etc/dhcp3/dhcpd.conf on the server, restarting both and checking that PC1 on the lan has an address from the new address range.

So what is really confusing me is that PC1 can communicate enough to get an IP address, but I am unable to ping PC1 from the server or vice verca.

'ifconfig' on the server shows this:
eth0      Link encap:Ethernet  HWaddr xxxxxxxxxx  
          inet addr:192.168.7.251  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe0f:9a5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43094 errors:0 dropped:522816568 overruns:0 frame:0
          TX packets:35790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45639537 (45.6 MB)  TX bytes:4777658 (4.7 MB)
          Interrupt:220 

eth1      Link encap:Ethernet  HWaddr xxxxxxxxxx
          inet addr:192.168.7.250  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe09:d40d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:366925 (366.9 KB)  TX bytes:48106 (48.1 KB)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76881 (76.8 KB)  TX bytes:76881 (76.8 KB)


'route' on the Server gives:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     *               255.255.255.0   U     0      0        0 eth0
192.168.7.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.7.254   0.0.0.0         UG    100    0        0 eth0

'ping -I eth1 192.168.7.46' from the server starts like this:
PING 192.168.7.46 (192.168.7.46) from 192.168.7.251 eth1: 56(84) bytes of data.
Then hangs indefinitely.


ifconfig on PC1 gives:
eth0      Link encap:Ethernet  HWaddr xxxxxxxxxx
          inet addr:192.168.7.46  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe45:6d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142126 (142.1 KB)  TX bytes:567342 (567.3 KB)
          Interrupt:10 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:408394 (408.3 KB)  TX bytes:408394 (408.3 KB)


route on PC1 gives
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     *               255.255.255.0   U     1      0        0 eth0
default         192.168.7.254   0.0.0.0         UG    0      0        0 eth0

and 'ping 192.168.7.250' on PC1 gives:
PING 192.168.7.250 (192.168.7.250) 56(84) bytes of data.
From 192.168.7.46 icmp_seq=1 Destination Host Unreachable

Can anyone suggest what I should check next please?

---

### Post by Iowan on 2008-12-19
How do machines connect - each connects to router?

Nope, I see PC1 connects to server.  Both machines seem to be using the router as gateway, but packets can't get from router to PC1 (or vice-versa).
PC1 should probably use 192.168.7.250 as it's gateway (meaning /etc/dhcp3/dhcpd.conf will need editing), and the server will need to be set up to forward packets on to the router ([this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") may help).

---

### Post by albinootje on 2008-12-19
Is there a specific reason that all of your computer included the router are in the same network-range ?

And i've seen DHCP-offers being taken while not being able to ping (With Linksys boxes and OpenWRT in trouble-shooting troubles "bricked" situations).

Your pc is connected with a cross-link cable to your 2nd NIC of your server ? Or is there a hub or switch in use ?

---

### Post by Iowan on 2008-12-19
Good point - having both server NICs in same subnet will likely cause issues.

---

### Post by mootpoint on 2008-12-20
Change your IP ranges to something like this:

192.168.7.x/24 hosts --> 192.168.7.254 (linux eth0) --> 192.168.8.1/24 (linux eth1) --> 192.168.8.254/24 (DSL router)

route add default gw 192.168.8.254 (on the linux box)

You may need to change your NAT settings on your DSL router. You could also change your LAN to something other than 192.168.7.x and leave the addressing alone on the router if you prefer. 

m00t

---

### Post by trubshac on 2008-12-20
Wow!  Thank you everyone!

Thanks to you generously giving your time and expertise, I now have a working network, and am another step closer to my goal.

For completeness, here is my configuration in case it helps anyone else trying to do the same.
In addition to the help I received here, I also followed some of this thread: [http://ubuntuforums.org/archive/index.php/t-713874.html](http://ubuntuforums.org/archive/index.php/t-713874.html)

Now, I can not only ping, but have full internet access from all machines on my lan (PC1 etc).

The key thing seems to be having different network ranges on each network.  So this is my working setup:


DSL ROUTER                     
192.168.7.254 static

SERVER
192.168.7.251  eth0 static to DSL router
192.168.8.250  eth1 static DHCP server to my lan

PC1 
192.168.8.46 DHCL client


Important bits from /etc/dhcp3/dhcpd.conf:

option domain-name-servers 212.139.132.5, 74.86.49.108;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
authoritative;

subnet 192.168.8.0 netmask 255.255.255.0 {
    range 192.168.8.50 192.168.8.99;
    option broadcast-address 192.168.8.255;
    option routers 192.168.8.250, 192.168.7.254;
    option subnet-mask 255.255.255.0;

 host PC1 {
	hardware ethernet xx:xx:xx:xx:xx:xx;
	fixed-address 192.168.8.46;
 }
}

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address	192.168.7.251
	netmask	255.255.255.0
	network 192.168.7.0
	broadcast 192.168.7.255
	gateway	192.168.7.254

auto eth1
iface eth1 inet static
	address 192.168.8.250
	netmask 255.255.255.0
	network 192.168.8.0
	broadcast 192.168.8.255


I enabled port forwarding in /etc/rc.local with:
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE
exit 0

And also made sure that the following was present in /etc/sysctl.conf
net.ipv4.ip_forward=1
net.ipv4.conf.default.fowarding=1
net.ipv4.conf.all.fowarding=1

Once again, thank you everyone.

---

