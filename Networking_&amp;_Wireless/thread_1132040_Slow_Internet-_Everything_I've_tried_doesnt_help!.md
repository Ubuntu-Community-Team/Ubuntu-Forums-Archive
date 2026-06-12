---
title: "Slow Internet- Everything I've tried doesnt help!"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by pah99 on 2009-04-21
Hey folks. I am currently running Jaunty, and I have a Dell Studio 1535 with a BCM 4322 B/G/N card. And I have slow internet. 

Now, I know that this is specific to Ubuntu because I had the issue in 8.10, and because Vista works fine. My wifi router is fine, and I get a speed of at least 54 Mb/s. But loading pages in Firefox takes forever, and synaptic takes forever to download updates.

What I have tried: I shut off Ipv6 in Firefox, and have tried both 3.x (current) and 3.5 (unstable). I have changed my DNS to OpenDNS. I have even gone to the trouble of building my own kernel and shutting off Ipv6. None of this helped. 

This is one of the last things that's keeping me from switching completely from Vista (the other being gaming). 

So any ideas would be great.

pasha@pasha-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:7e:f5:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:3e:4d:83  
          inet addr:172.16.1.108  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::222:69ff:fe3e:4d83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6689 errors:0 dropped:0 overruns:0 frame:9606
          TX packets:5131 errors:53 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4596093 (4.5 MB)  TX bytes:847531 (847.5 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:428900 (428.9 KB)  TX bytes:428900 (428.9 KB)

---

### Post by sir_nasty on 2009-04-21
strange looking ip..... try setting up your linux box on the exact same ip as your vista and see if that makes a difference...  perhaps it's an IP specific router issue?

---

### Post by pah99 on 2009-04-21
Okay, this is weird. I have conky setup to give me my ip, and it says 172.16.1.108 (as does the ifconfig). But when I go to OpenDNS or any other website to check my IP, I get 134.241.100.250. What's going on?

---

### Post by Joushou on 2009-04-21
172.16.1.108 is your internal (NAT'd/Masq'd), 134.241.100.250 is your external IP.
What does a ping to the router give you, and a ping of google (just to check where the slowdown is)?

---

### Post by pah99 on 2009-04-21
I couldn't do my router (I'm currently not home).

pasha@pasha-laptop:~$ ping -c 5 [www.google.com](www.google.com)
PING google.navigation.opendns.com (208.69.32.230) 56(84) bytes of data.
64 bytes from google.navigation.opendns.com (208.69.32.230): icmp_seq=1 ttl=50 time=21.3 ms
64 bytes from google.navigation.opendns.com (208.69.32.230): icmp_seq=2 ttl=50 time=22.2 ms
64 bytes from google.navigation.opendns.com (208.69.32.230): icmp_seq=3 ttl=50 time=23.3 ms
64 bytes from google.navigation.opendns.com (208.69.32.230): icmp_seq=4 ttl=50 time=22.1 ms
64 bytes from google.navigation.opendns.com (208.69.32.230): icmp_seq=5 ttl=50 time=23.0 ms

--- google.navigation.opendns.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 21.366/22.422/23.316/0.703 ms

I mean, looking from this, is there anything you can tell?

---

### Post by sir_nasty on 2009-04-21
response times look good, you could try running a 'traceroute [www.google.com](www.google.com)' then run it from your "working" machine and see if the response times look much different, might show you where you're getting a slowdown, also, as a precaution to eliminate a hardware issue swap ports on your router, plug the good machine into the bad machines port and bad into good then see if that makes a difference.

---

### Post by pah99 on 2009-04-26
Sorry for taking so long. 

Updated ifconfig from home:
> pasha@pasha-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:7e:f5:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:3e:4d:83  
          inet addr:192.168.10.200  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe3e:4d83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16608 errors:1 dropped:0 overruns:0 frame:4040
          TX packets:13463 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19075182 (19.0 MB)  TX bytes:1870556 (1.8 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)

Pinging my router:
> pasha@pasha-laptop:~$ ping -c 5 192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_seq=1 ttl=64 time=0.554 ms
64 bytes from 192.168.10.1: icmp_seq=2 ttl=64 time=0.757 ms
64 bytes from 192.168.10.1: icmp_seq=3 ttl=64 time=0.544 ms
64 bytes from 192.168.10.1: icmp_seq=4 ttl=64 time=0.564 ms
64 bytes from 192.168.10.1: icmp_seq=5 ttl=64 time=2.89 ms

--- 192.168.10.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.544/1.063/2.896/0.919 ms

And pinging [www.google.com](www.google.com) (from home):
> pasha@pasha-laptop:~$ ping -c 5 [www.google.com](www.google.com)
PING google.navigation.opendns.com (208.67.217.231) 56(84) bytes of data.
64 bytes from google.navigation.opendns.com (208.67.217.231): icmp_seq=1 ttl=50 time=12.0 ms
64 bytes from google.navigation.opendns.com (208.67.217.231): icmp_seq=2 ttl=50 time=14.6 ms
64 bytes from google.navigation.opendns.com (208.67.217.231): icmp_seq=3 ttl=50 time=12.5 ms
64 bytes from google.navigation.opendns.com (208.67.217.231): icmp_seq=4 ttl=50 time=13.2 ms
64 bytes from google.navigation.opendns.com (208.67.217.231): icmp_seq=5 ttl=50 time=12.7 ms

--- google.navigation.opendns.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 12.011/13.048/14.668/0.911 ms

And one more for the fun of it:

> pasha@pasha-laptop:~$ ping -c 5 [www.spike.com](www.spike.com)
PING a1415.g.akamai.net (216.246.75.66) 56(84) bytes of data.
64 bytes from 216.246.75.66: icmp_seq=1 ttl=51 time=13.2 ms
64 bytes from 216.246.75.66: icmp_seq=2 ttl=51 time=13.0 ms
64 bytes from 216.246.75.66: icmp_seq=3 ttl=51 time=13.2 ms
64 bytes from 216.246.75.66: icmp_seq=4 ttl=51 time=15.3 ms

--- a1415.g.akamai.net ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 85134ms
rtt min/avg/max/mdev = 13.097/13.734/15.346/0.932 ms

I'm not exactly sure of how to do a traceroute in Vista, but here it is in Ubuntu:
> pasha@pasha-laptop:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (208.67.217.231), 30 hops max, 60 byte packets
 1  192.168.10.1 (192.168.10.1)  0.736 ms  1.240 ms  1.228 ms
 2  c-3-0-ubr01.monson.ma.boston.comcast.net (73.171.68.1)  10.522 ms  10.640 ms  10.692 ms
 3  ge-2-37-ur01.monson.ma.boston.comcast.net (68.87.150.225)  11.306 ms  11.381 ms  11.506 ms
 4  te-9-2-ur01.springfield.ma.boston.comcast.net (68.87.144.250)  11.570 ms  11.677 ms  14.074 ms
 5  te-8-1-ar01.springfield.ma.boston.comcast.net (68.85.162.54)  14.064 ms  14.945 ms  15.006 ms
 6  be-11-ar99.chartford.ct.hartford.comcast.net (68.87.146.26)  16.390 ms  9.700 ms  10.441 ms
 7  pos-1-5-0-0-cr01.newyork.ny.ibone.comcast.net (68.86.90.65)  13.941 ms  14.074 ms  14.062 ms
 8  162.97.117.101 (162.97.117.101)  21.269 ms  21.343 ms  21.331 ms
 9  xe-8-1.r02.nycmny01.us.bb.gin.ntt.net (129.250.8.129)  18.926 ms  19.005 ms  18.993 ms
10  fa-0.opendns.nycmny01.us.bb.gin.ntt.net (129.250.12.250)  18.204 ms  18.194 ms  18.332 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

Took about a minute to do, and from the looks of things, it didn't even finish. 

So, this is my issue. I have random time-outs and pages like to take forever to load, but randomly. When I just start up Ubuntu, things are smooth and fast. After I open up my email and a couple other sites, things slow down, and then stop. After a minute or two, I can refresh, and it will, but then things will stop again. Its very very agitating and annoying. The funny part is, when I access my router from my laptop, even that slows down and stops.

Any more ideas anyone?

---

### Post by uniden9 on 2009-04-27
Sounds like this could possibly be an issue with ipv6 being enabled and your router or isp not supporting it.  Try disabling ipv6 stack.

To instantly disable ipv6 in jaunty, this is only for the current boot only:
#sudo echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

To undo, just simply reboot.

To make this change permanent, you will need to add some kernel options.

#sudo echo net.ipv6.conf.default.disable_ipv6 = 1 >> /etc/sysctl.conf
#sudo sysctl -p

Justin

---

### Post by pah99 on 2009-04-27
> **uniden9 said:**
> Sounds like this could possibly be an issue with ipv6. Try disabling ipv6 stack.

I tried both methods. At first, it seemed to be helping, but then soon after things turned to sh*t. Still have the issue. And like I said, i have tried building kernels before and disabling IPv6, but that didn't help.

---

### Post by uniden9 on 2009-04-28
To be honest with you, I've never had a happy experience with wireless. The only thing I could see is may be this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291760)

I look and see if you are getting any of those type messages in your logs. 


Justin

---

