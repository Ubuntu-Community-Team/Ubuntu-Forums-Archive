---
title: "Problem getting DHCP to assigh IP address"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by peterv6 on 2010-03-22
I'm using Ubuntu 9.10, and I want DHCP to assign an IP address automatically.  I can ping my router, and get a reply.  I just have no idea how to do this.  I've searched other Linux forums and didn't find anything relevant.  Can someone help me?  I need really basic instructions.  I'd appreciate any help.  I'm trying to get my Ubuntu machine onto my Windows network.
Thanks....

---

### Post by chili555 on 2010-03-23
If you can ping your router and get replies, don't you have an IP address? Did you assign it manually? Please post:```
ifconfig
ping -c3 ip.address.of.router
cat /etc/resolv.conf
```> I'm trying to get my Ubuntu machine onto my Windows network.Do you mean to share files, etc.? That is a whole different subject than getting an IP address. Please clarify.

---

### Post by peterv6 on 2010-03-23
You are correct, I *do* have an ip address, but I need an ip address in my local networks range (Sorry, should have been a little more specific).  The current ip is 10.211.55.4 (I did not assign it manually).  What I'm looking for is something like 192.168.1.157.

```
peterv@MBP17UBUNTU<216>$: ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1c:42:88:8b:22  
          inet addr:10.211.55.4  Bcast:10.211.55.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:42ff:fe88:8b22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1936296 (1.9 MB)  TX bytes:272033 (272.0 KB)
          Interrupt:10 Base address:0x8200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


Tue Mar 23 13:18:20 EDT 2010 
~ ->
peterv@MBP17UBUNTU<217>$: ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=8.93 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=2.03 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=3.27 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.031/4.746/8.935/3.005 ms

Tue Mar 23 13:18:20 EDT 2010 
~ ->
peterv@MBP17UBUNTU<218>$: cat /etc/resolv.conf
domain localdomain
search localdomain
nameserver 10.211.55.1

Tue Mar 23 13:18:20 EDT 2010 
~ ->
peterv@MBP17UBUNTU<219>$: 

Tue Mar 23 13:18:20 EDT 2010 
~ ->
peterv@MBP17UBUNTU<219>$: 

```

I'm interested in getting an "in-network" ip address first, then in file sharing.  Any help you can provide is greatly appreciated.

---

### Post by chili555 on 2010-03-23
How is this even possible?? What in the wide world of sports is agoin' on here??

Please explain your setup. The computer attaches to a router? The router attaches to...what? A DSL modem or cable modem or...??

I hate to even suppose this, but does the cable modem hand out a 10.x address to the router and the router hands out a 192.x address to computers? Is your computer getting the wrong address because it's connected to the wrong port on the router? Excuse me if I am barking up the wrong tree.

---

### Post by Iowan on 2010-03-23
You could down the interface, then manually run dhclient (from a terminal) to see where the address comes from.

---

### Post by peterv6 on 2010-03-23
My computer is a MacBook Pro with wireless networking.  It's attached to a Linksys wireless router, which is connected to a DSL modem.

I'm running Snow Leopard, and the ip address for that is 192.168.1.100.  I'm running Ubuntu 9.10 via Parallels 5.0 and that ip address is 10.211.55.4.  I'm also running Windows XP Pro SP3 via Parallels 5.0 and that ip is 192.168.1.102.

The only OS with a problem getting an IP address from the router is Ubuntu.

Iowan, I'm a rookie with networking (obviously), can you explain how to "down the interface".

Your replies are appreciated.

---

### Post by chili555 on 2010-03-23
So Parallels is, in effect, a virtual machine? Snow Leopard is the host OS and Ubuntu is the guest?

'Down the interface' means:```
sudo ifconfig eth0 down
```Then, do:```
sudo dhclient -r eth0
sudo ifconfig eth0 up
sudo dhclient eth0
```We are interested in the details, whether it connects or not.

---

### Post by peterv6 on 2010-03-23
You are correct.  Ubuntu is a guest, as is Windows XP.  Snow Leopard is the host.  The output of your commands follows:```
Tue Mar 23 14:46:26 EDT 2010 
~ ->
peterv@MBP17UBUNTU<278>$: sudo ifconfig eth0 down

Tue Mar 23 14:46:26 EDT 2010 
~ ->
peterv@MBP17UBUNTU<279>$: sudo dhclient -r eth0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1c:42:88:8b:22
Sending on   LPF/eth0/00:1c:42:88:8b:22
Sending on   Socket/fallback

Tue Mar 23 14:46:26 EDT 2010 
~ ->
peterv@MBP17UBUNTU<280>$: sudo ifconfig eth0 up

Tue Mar 23 14:46:26 EDT 2010 
~ ->
peterv@MBP17UBUNTU<281>$: sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1c:42:88:8b:22
Sending on   LPF/eth0/00:1c:42:88:8b:22
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.211.55.4 from 10.211.55.1
DHCPREQUEST of 10.211.55.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.211.55.4 from 10.211.55.1
bound to 10.211.55.4 -- renewal in 239896 seconds.

Tue Mar 23 14:46:26 EDT 2010 
~ ->
peterv@MBP17UBUNTU<282>$: 

```

---

### Post by chili555 on 2010-03-23
I know nothing about Parallels and little about virtual machines, but it appears you have Bridged Ethernet Networking: [http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22251.htm](http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22251.htm)> When operating in the Bridged Ethernet mode, your virtual machine appears on the network as a stand-alone computer with its own IP address and network nameI think you really want Shared Networking: [http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22247.htm](http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22247.htm)> In this mode your virtual machine can access other computers on your local network and the Internet by using the IP address of the physical computer. The virtual machine itself does not have its own IP address on the network.I have no idea how to switch it.

---

### Post by Iowan on 2010-03-23
10.211.55.1 is the DHCP server - which machine is that?

---

### Post by peterv6 on 2010-03-23
Chili555, My Ubuntu VM is actually set up with shared networking.  I may have to contact Parallels support.

Iowan, That IP address is in the resolv.conf file.  I'm thinking that if that's changed to what it is in the OS X resolv.conf file, that might fix this.  What do you guys think?

Just for curiosity's sake, I ran the 3 commands chili555 suggested in a terminal in Snow Leopard.  Would you mind taking a look at the output from that, and see if anything comes to mind? ```
Tue Mar 23 14:39:09 EDT 2010 
~ ->
peterv@MBP17.local<519>$: ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	inet6 ::1 prefixlen 128 
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::21f:5bff:fec4:5426%en1 prefixlen 64 scopeid 0x4 
	inet 192.168.1.100 netmask 0xffffff00 broadcast 192.168.1.255
	ether 00:1f:5b:c4:54:26 
	media: autoselect status: active
	supported media: autoselect
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:1f:5b:ef:f8:ca 
	media: autoselect status: inactive
	supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
	lladdr 00:1f:f3:ff:fe:16:ee:b0 
	media: autoselect <full-duplex> status: inactive
	supported media: autoselect <full-duplex>
vnic0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::21c:42ff:fe00:8%vnic0 prefixlen 64 scopeid 0x7 
	inet 10.211.55.2 netmask 0xffffff00 broadcast 10.211.55.255
	ether 00:1c:42:00:00:08 
	media: autoselect status: active
	supported media: autoselect
vnic1: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 10.37.129.2 netmask 0xffffff00 broadcast 10.37.129.255
	ether 00:1c:42:00:00:09 
	media: autoselect status: active
	supported media: autoselect
vmnet1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 192.168.253.1 netmask 0xffffff00 broadcast 192.168.253.255
	ether 00:50:56:c0:00:01 
vmnet8: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 192.168.157.1 netmask 0xffffff00 broadcast 192.168.157.255
	ether 00:50:56:c0:00:08 

Tue Mar 23 14:39:09 EDT 2010 
~ ->
peterv@MBP17.local<520>$: ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
64 bytes from 192.168.1.1: icmp_seq=0 ttl=64 time=4.151 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.382 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=5.135 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 1.382/3.556/5.135/1.589 ms

Tue Mar 23 14:39:09 EDT 2010 
~ ->
peterv@MBP17.local<521>$: cat /etc/resolv.conf
#
# Mac OS X Notice
#
# This file is not used by the host name and address resolution
# or the DNS query routing mechanisms used by most processes on
# this Mac OS X system.
#
# This file is automatically generated.
#
nameserver 71.243.0.12
nameserver 71.250.0.12

Tue Mar 23 14:39:09 EDT 2010 
~ ->
peterv@MBP17.local<522>$:
```

The one thing that stands out to me is that last 2 lines of this output.  Might that be what's needed in the UBUNTU resolv.conf file?

Thanks again for all the help!

---

### Post by peterv6 on 2010-03-23
All,
I've figured out what the problem was.  Chilli555 got me on the track.  He said "it appears you have Bridged Ethernet Networking" and "I think you really want Shared Networking".  Actually, I *had* shared networking, but when I changed it to "Airport Bridged", it solved the problem.  I got an IP of 192.168.1.104, and the name files in the resolv.conf file now match the DNS ip addresses of the router.  This is exactly what I want.  Now all I need to do is figure out how to set up filesharing.  

Can you tell me if I need to install Samba to get filesharing?  I can see my Windows workgroup in the network file directory, but when I click it, I can't access it.

Thanks for everything!
Peter V.

---

### Post by chili555 on 2010-03-23
> Can you tell me if I need to install Samba to get filesharing?Yessir. There are a few dozen posts a day here outlining other steps in case it doesn't spring to life automagically.

Glad it's working!

---

