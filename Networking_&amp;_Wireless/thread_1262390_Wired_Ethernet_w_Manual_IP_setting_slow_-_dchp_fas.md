---
title: "Wired Ethernet w/ Manual IP setting slow - dchp faster - any suggestions?"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by pm124493 on 2009-09-09
I am very confused. I have been using Ubuntu since v6 and Linux in some form since 1992. I always use manual ip configurations because I share printers and folders on other ubuntu and windows PC(s) in the home. Until Jaunty I never had a problem. The Network Manager in v8.04 and v9.04 have been flakey at best. I have read numerous posts on manual configurations. Samba works fine and internal IP to IP works fine. 
The problem:
Using Firefox or Chrome browsers to access the Internet runs very slow taking up to 30 or more seconds to resolve addresses. I verified my routers settings for nameservers and even tried the Open Nameservers with no affect. My Vista machine uses manual IP with the same settings as the Ubuntu 9.04 box with no problems resolving addresses. My wifes Ubuntu 9.04 box has no problem resolving IP addresses. Her PC I use the Network Manager with a manual IP and manual nameservers.
My /etc/network/interfaces file:
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

My /etc/resolv.conf file:
domain hsd1.ga.comcast.net.
search hsd1.ga.comcast.net.
nameserver 208.67.222.222
nameserver 208.67.220.220

I have changed the resolv.conf file not to use the "domain" or "search" parameters with no effect on the problem. If I use the nameservers from the router that comcast has it does not change or relieve the problem.

If I use DHCP then the problem changes to five (5) seconds to resolve address from thirty (30) or more.

***_My request is: "Are there any diagnostics or programs I can run to try and figure out why manual IP is so slow resolving addresses?"_***

Ping to router:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.27 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.02 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.02 ms
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5005ms
rtt min/avg/max/mdev = 1.018/1.137/1.441/0.164 ms

Ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:16:e6:d7:67:2a  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5347855 (5.3 MB)  TX bytes:900656 (900.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1094493 (1.0 MB)  TX bytes:1094493 (1.0 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.22.1  Bcast:172.16.22.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.223.1  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have VMWare with an XP guest. Running IE under vmware to resolving IP addresses is <5 seconds.

I have also modified Firefox with every know recommended change to speed it up.

Thanks in Advance for your suggestions or recommendations!

Ubuntu 9.04 64 bit
Gigabyte P965-D3SL MB. 4 GB DDR2 800 memory
Intel Q6600 2.4Ghz Quad Processor
Nvidia 9600GT
Maxtor 200GB SATAII, Maxtor 300GB SATAII
DVD R-RW SATA

---

### Post by dbalascak on 2009-09-09
Can you post the output of *netstat rn*
Also what do *ifconfig -a* and *netstat -rn*look like with the DHCP address.

---

### Post by pm124493 on 2009-09-10
Thank you for your interest in my problem. Your wish is my command.

netstat -rn output:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.22.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.223.0   0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


ifconfig -a DHCP output: (Note the ifconfig above is from DHCP config. The only difference with the manual ip config output is the inet addr: is 192.168.1.3)

eth0      Link encap:Ethernet  HWaddr 00:16:e6:d7:67:2a  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9504410 (9.5 MB)  TX bytes:1606245 (1.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:354237 (354.2 KB)  TX bytes:354237 (354.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.22.1  Bcast:172.16.22.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.223.1  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Router setup: COMCAST
   	   	   	   	   	 
Internet Connection Type :DHCP	  	
Optional Settings
(required by some ISPs)
	  	  	 Router Name:  	WRTG54	  	 
  	  	  	 Host Name:  		  	 
	  	  	 Domain Name:  		  	 
	  	  	 MTU: 	MANUAL	  	 
	  	  	 Size: 	1500	  	 
  	  	
Network Setup 	  	  	  	  	  	  	  	 
Router IP 	  	  	 Local IP Address: 192.168.1.1 	  	 
	  	  	         Subnet Mask: 255.255.255.0
Network Address
Server Settings (DHCP) 	  	  	 DHCP Server: 	Enable 	  	 
	  	  	 Starting IP Address: 	 192.168.1.100	  	 
	  	  	 Maximum Number of  DHCP Users:5  	  	 
	  	  	 Client Lease Time: 0	  minutes (0 means one day) 	  	 
	 	 	 Static DNS 1: 	  208.67.222.222 	 	 
	 	 	 Static DNS 2: 	  208.67.220.220 	 	 
	 	 	 Static DNS 3: 	  . . . 	 	 
	  	  	 WINS:  	  . . . 	  	 
  	  	
  	  		 
	 
Time Setting 	  	  	 Time Zone: EDT(-5)   	  	  	 
	  	  	Automatically adjust clock for daylight saving changes

---

### Post by Iowan on 2009-09-10
Does the **netstat -rn** output (or **route -n**) change between static and DHCP addresses?

---

### Post by pm124493 on 2009-09-11
netstat -rn output manual ip:
 netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.22.0     0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.223.0   0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

No difference between manual or dhcp ip.

---

### Post by dbalascak on 2009-09-12
If you do an *nslookup [www.google.com](www.google.com)* with each config, does one show using a different DNS?

---

### Post by zman58 on 2009-09-12
What does your network look like?
Do you have a router, cable modem, gateway server?
How are the devices arranged? Even when you say it is fast with DHCP, it actually sounds very slow (5 seconds to resolve).

Could be something with your gateway service at (192.168.1.1). Are you using a WAN router?

Try traceroute to the remote DNS server. Maybe it will show you where the long delay is.

System -> Administration -> Network Tools -> Traceroute(tab)

---

### Post by pm124493 on 2009-09-15
Here is traceroute with manual ip:
UBUNTU Traceroute to 68.87.68.166
Hop	Hostname	IP	Time 1	Time 2
1	UBUNTU.local	192.168.1.3	0.111ms	
1	192.168.1.1	192.168.1.1	2.571ms	
1	192.168.1.1	192.168.1.1	1.942ms	
2	no	reply	*	
3	no	reply	*	
4	te-0-8-0-2-crs01.d1stonemtn.ga.atlanta.comcast.net	68.86.107.98	15.674ms	
5	no	reply	*	
6	no	reply	*	
7	no	reply	*	
8	no	reply	*	
9	no	reply	*	
10	no	reply	*	
11	no	reply	*	
12	no	reply	*	
13	no	reply	*	
14	no	reply	*	
15	no	reply	*	
16	no	reply	*	
17	no	reply	*	
18	no	reply	*	
19	no	reply	*	
20	no	reply	*	
21	no	reply	*	
22	no	reply	*	
23	no	reply	*	
24	no	reply	*	
25	no	reply	*	
26	no	reply	*	
27	no	reply	*	
28	no	reply	*	
29	no	reply	*	
30	no	reply	*	
31	no	reply	*	

Here is traceroute from VISTA PC on same hub.
Tracing route to cns.s3woodstock.ga.atlanta.comcast.net [68.87.68.166]
over a maximum of 30 hops:
 
1     1 ms     1 ms    <1 ms  192.168.1.1 
  
2     *        *        *     Request timed out.
  
3    11 ms    11 ms     8 ms  68.85.68.201 
  
4    10 ms    11 ms    11 ms  te-0-8-0-2-crs01.d1stonemtn.ga.atlanta.comcast.net [68.86.107.98] 
  
5    12 ms    10 ms    11 ms  te-8-1-ur02.S3NDigital.ga.atlanta.comcast.net [68.86.107.25] 
  
6    10 ms    12 ms    10 ms  GE-1-46-ur01.s3ndigital.ga.atlanta.comcast.net [68.86.110.201] 
  
7    10 ms    11 ms    11 ms  cns.s3woodstock.ga.atlanta.comcast.net [68.87.68.166] 
Trace complete.

Network setup:
UBUNTU and VISTA PCs tied to HUB. HUB Tied to LINKSYS WRTG54 Router. Second UBUNTU PC tied to LINKSYS Router. Router tied to COMCAST Modem.

My issue is why UBUNTU PC has such a bad traceroute while the VISTA PC on the same HUB is okay!

---

### Post by pm124493 on 2009-09-16
I could not figure out what the problem was. I appreciate everyone's input. I re-installed UBUNTU 9.04 and all is working great. The traceroute still looks bad wither I use DCHP or manual IP, but the response is great.

My assumption is that I installed something that impacted TCPIP. Firefox is now responding fast without having to change any settings. 

I would have been happier to figure out what the problem was, but time is money.

The re-loading of the OS used to be a Windoze problem solver I used it often enough. This is the first time I had to re-load UBUNTU to resolve a problem. Hope this is not the indication of future UBUNTU release issues.

Again thank you to all that tried to help.:(

---

### Post by aprend_edd on 2009-09-19
Hi, I'm from Colombia, I am new to this forum and need help. I recently installed ubuntu and my problem is that the OS does not detect the Target is a LAN Atheros and i can't configure the connection either. Likewise, the driver's target doestn't on the manufacturer's website to download it and I have not found any of it online. So if someone can help me I will be very greatfull.
 
PD: If there's some that can answer me in spanish will be great, but if is in english there's no problem.
 
thanks.

---

