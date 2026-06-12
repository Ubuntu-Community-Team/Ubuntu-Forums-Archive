---
title: "pings router but no internet wont load on the browser"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by 007casper on 2009-07-06
not to upstage the thread.  However, I have the same problem that cartmanx is facing. 

My default internal connection to my IP 192.168.1.1.  

I also remove Network-Manager. Disabled firewall.  I have been working on it for hours.  I cant seem to load anything on the browser.

---

### Post by jonobr on 2009-07-06
Hello


Actually ,

You could be experiencing a different problem.

Can you put the url in a different browser and get the same result?
Can you put the ip address of google or something else in your browser?
Does it do the same thing?

when you type nslookup pingplotter
does it resolve correctly?

Can you ping the ip address of pingplotter returned in the nslookup?

if so, can you do w3m pingplotter in a terminal window?

It should show you something like in the attached image


Lastly, (and Im mean this respectfully)
Imagine you opened this thread, and I was helping someone else who may or may not have a similar problem.

I would open another thread, with the problem described and responses to the question as part of the post.... keep it pithy.

I believe the charge for opening a new post has dropped dramatically :-)

---

### Post by 007casper on 2009-07-06
pings router but no internet wont load on the browser.  I have the similar problem another member facing over at [9.04 Server Can ping router but no Internet.]("http://ubuntuforums.org/showthread.php?t=1205758")

However, I can ping to yahoo.com etc... but cant load internet on the browser.

Disabled NetworkManager. Disabled firewall.

**sudo iptables -L**
> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

**cat /etc/network/interfaces**
> 
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


**tcpdump -vvxXns0 -i eth0**
> 
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes


**arp -na**
> 
? (192.168.1.200) at 00:22:b0:cb:ed:63 [ether] on eth1
  
**mtr --report -c 5 -r 74.125.45.100**
> 
HOST: sunnie      Loss% Snt Last Avg Best Wrst StDev
1. 192.168.1.1 	   0.0%   5 0.7  0.8  0.6  1.2   0.2
2. ??? 		 100.0%   5 0.0  0.0  0.0  0.0   0.0

:shock:

OMG! everything is broken! Please, advise.  Thank you.

---

### Post by 007casper on 2009-07-06
fair enough... thanks for the help jonobr.  
I moved my thread to [internet wont work on the browser]("http://ubuntuforums.org/showthread.php?p=7571233#post7571233"), and gave a link back to this thread.  

I really appreciate if anyone can help.  Because, I am lost. 

I am checking nslookup pingplotter. Thank you.

---

### Post by jonobr on 2009-07-06
Hello


Could you try the tcpdump using an -i eth1 as you did it on eth 0 but that does appear to be configured.
Thats probably why its not showing output below

Also recommend doing a tcpdump -w trace.pcap -s 1600 -i eth1 and looking at posting the results

Thanks

---

### Post by 007casper on 2009-07-06
I am not in front of that computer at the moment.  I will post the output as soon as I get back to it.  However, I have one more question that is related to this issue. I was checking the [net config manual]("https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html")  The gateway IP same as nameserver.

> iface eth1 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1


search mydomain.example
nameserver 192.168.0.1
nameserver 4.2.2.2

Isnt nameserver suppose to be the DNS server IP? 

Thanks

---

### Post by alphacrucis2 on 2009-07-06
> **007casper said:**
> I am not in front of that computer at the moment.  I will post the output as soon as I get back to it.  However, I have one more question that is related to this issue. I was checking the [net config manual]("https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html")  The gateway IP same as nameserver.



Isnt nameserver suppose to be the DNS server IP? 

Thanks

Yes but many SOHO routers act as a nameserver for the local devices. My one does and then forwards DNS requests upstream to my ISP's dns servers.

---

### Post by jonobr on 2009-07-06
Hey alphacrucis2

Mine operates the same way.
It goes to 192.168.0.1

DNS is hirearchical anyway, the dns request goes up to resolve and sometimes generates a cache on your local network.

Thats why when you are doing resolution testing,its always a good idea to use different names when trying to see if resolution is working.

---

### Post by Sef on 2009-07-06
Merged threads.  The correct procedure would have been to click on the report notebook and ask that your posts be moved to their own thread.

---

### Post by 007casper on 2009-07-06
Merging the thread threw me off a bit.  Thank you.  I was like what happened here.

I really appreciate all the help.  I have been working on it so long that I am getting a bit confused.

here we go...

**sudo tcpdump -vvxXns0 -i eth1**
> 
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
16:42:08.332713 IP (tos 0x0, ttl 150, id 5073, offset 0, flags [none], proto UDP (17), length 76) 192.168.1.1.4241 > 0.0.0.0.123: [udp sum ok] NTPv1, length 48
	Client, Leap indicator:  (0), Stratum 0, poll 0s, precision 0
	Root Delay: 0.000000, Root dispersion: 0.000000, Reference-ID: (unspec)
	  Reference Timestamp:  0.000000000
	  Originator Timestamp: 0.000000000
	  Receive Timestamp:    0.000000000
	  Transmit Timestamp:   2208988816.000000000 (1969/12/31 16:00:16)
	    Originator - Receive Timestamp:  0.000000000
	    Originator - Transmit Timestamp: 2208988816.000000000 (1969/12/31 16:00:16)
	0x0000:  4500 004c 13d1 0000 9611 4f27 c0a8 0101  E..L......O'....
	0x0010:  0000 0000 1091 007b 0038 1f8e 0b00 0000  .......{.8......
	0x0020:  0000 0000 0000 0000 0000 0000 0000 0000  ................
	0x0030:  0000 0000 0000 0000 0000 0000 0000 0000  ................
	0x0040:  0000 0000 83aa 7e90 0000 0000            ......~.....
^C
1 packets captured
1 packets received by filter
0 packets dropped by kernel


update on the eth0.  

**sudo tcpdump -vvxXns0 -i eth0**
> 
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes

**sudo tcpdump -w trace.pcap -s 1600 -i eth1**> 
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 1600 bytes

tried arp -na again...  > 
? (192.168.1.200) at 00:22:b0:cb:ed:63 [ether] on eth1

Last night, after working on it several hours.  I figured I will look at it with a fresh mind.  It seems like I am back to square one.

---

### Post by 007casper on 2009-07-06
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5455
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:c6:d5:b9:90
Sending on   LPF/eth0/00:1f:c6:d5:b9:90
Sending on   Socket/fallback
SIOCDELRT: No such process
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:c6:d5:b9:90
Sending on   LPF/eth0/00:1f:c6:d5:b9:90
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
 * Stopping NTP server ntpd
   ...done.
                                                                         [ OK ]

and then it just hangs

* Starting NTP server ntpd
   ...done.
 * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

???

---

### Post by 007casper on 2009-07-06
fistik@www:~$ sudo ping 74.125.45.100> 
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.

then it stops.  I can ping the router without a problem.

nslookup pingplotter> 
;; connection timed out; no servers could be reached

w3m pingplotter> 
openning socket
w3m:Cant load pingplotter

ifconfig -a> 
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:90  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfa0000-fdfc0000 

eth1      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:91  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fed5:b991/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2634 (2.6 KB)  TX bytes:21023 (21.0 KB)
          Memory:fdfe0000-fe000000 

eth2      Link encap:Ethernet  HWaddr 00:1f:c6:d6:04:4a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdae0000-fdb00000 

eth3      Link encap:Ethernet  HWaddr 00:1f:c6:d6:03:76  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fd9e0000-fda00000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:90  
          inet addr:169.254.9.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:fdfa0000-fdfc0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:540 (540.0 B)  TX bytes:540 (540.0 B)

pan0      Link encap:Ethernet  HWaddr 8e:a4:88:5f:9e:bd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dig google.com> 
;;global options: printcmd
;;connection timed out; no servers could be reached


cat /etc/resolv.conf> 
domain socal.rr.com
search socal.rr.com
nameserver 192.168.1.1
nameserver 66.75.160.38
nameserver 66.75.160.39

cat /etc/network/interfaces
> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1 
iface eth1 inet static
	address 192.168.1.200
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1


---

### Post by 007casper on 2009-07-06
If something seems obvious, please let me know.  Right now, I am pulling my hair and dont know what *&# is going on....

---

### Post by 007casper on 2009-07-06
I changed the DNS on the router to opendns' IP set

still trouble shooting here...

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
[B]
mtr --report -c 5 -r 74.125.45.100[/B]
HOST: sunnie          Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     5    0.3   0.4   0.3   0.6   0.1
  2. ???                          100.0     5    0.0   0.0   0.0   0.0   0.0

**mtr --report -c 5 -r 192.168.1.1**
HOST: sunnie          Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     5    0.3   0.4   0.3   0.4   0.0

---

### Post by 007casper on 2009-07-07
**sudo tcpdump -w trace1.pcap -i any port 53**
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes

[B]
sudo tcpdump -w trace2.pcap -i any port 53[/B]
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes

By the way, I have four ethernet ports.  It worked like a charm at my house.  In the house I have DHCP set up on the router, and had static IP on the server.  Now, at the new location, if I make eth0 static, I cant seem to access the router via browser. Therefore, I have DHCP for eth0, and static IP for eth1. And I have a static IP on the router.   

please, advise.  I have been working on this for the past few days now. I really appreciate any input.  Thank you.

---

### Post by 007casper on 2009-07-07
here is the diagram

[IMG]http://#[/IMG]

---

### Post by 007casper on 2009-07-07
No love!... or is it just... No one has a clue over here.

---

### Post by 007casper on 2009-07-08
removed avahi... > 
sudo /etc/init.d/avahi-daemon stop
sudo update-rc.d -f avahi-daemon remove

Then, I was able to set eh0 to static.  Before, it wasn't able to set it static.  It would hick up here and there. At the moment, I cant access the router from the server.  However, I can access the router with my XP computer.  Does anyone know what is going on? How come XP can access it, but not Jaunty???

Any help would be great.  I'd really appreciate it. It is getting lonely over here.

---

### Post by 007casper on 2009-07-09
it works now.

It was avahi, network manager. You need to remove them.  Then, check if the ports are still at the same location on the server.  Bingo!  It is a go.  Thanks everyone. Especially, I thank **_jonobr_**.

---

