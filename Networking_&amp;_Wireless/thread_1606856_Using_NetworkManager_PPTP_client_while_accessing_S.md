---
title: "Using NetworkManager PPTP client while accessing SSH/Apache from public Internet"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by VAvenger on 2010-10-27
Probably a bad title, but I'm cramming a lot of info there.

I've searched the forums (250 thread limit) for a fix on this, but all the questions seem unanswered or unrelated.

My situation is this: I'm running Ubuntu x64 10.10 'Maverick'.

I have a cablemodem connection for my Internet access. I have home network running on DD-WRT with the dreadful Linksys WRT54G series router.

My DD-WRT router is 192.168.1.1, subnet 255.255.255.0.
My Linux box is 192.168.1.61, subnet 255.255.255.0.

I have a VyprVPN connection set up successfully on Linux. Mostly everything works great, speed's fine, latency is what I expect it to be.

Except... I also run an SSH server to remotely admin the box at port 22, an Apache server running over SSL at port 7001, and a Transmission web client at port 7002 (only secured by basic HTTP realms auth). All of these things worked before I got the VPN working, I'm of course using NAT at the DD-WRT router.

The endresult I am looking for, is to have the security and protection of the VPN (even if it's only perceived) for everything I do on this machine -- EXCEPT on Apache, the Transmission web panel, and the SSH server, which I want to access from the outside world.

I have no firewalls running or configured, not even iptables, not even the SPI firewall on DD-WRT.

All connections to the aforementioned services from the outside world timeout coming in to the Linux box. They all work from inside my home network (182.168.1.0/24).

In case it's needed, he's my routing:

owner@ethanol:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
216.168.2.17    192.168.1.1     255.255.255.255 UGH       0 0          0 eth1
216.168.2.17    192.168.1.1     255.255.255.255 UGH       0 0          0 eth1
192.168.35.47   0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0


And here's my iptables:
owner@ethanol:~$ sudo iptables --list
[sudo] password for owner: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


And my ifconfig:
owner@ethanol:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:**:**:**:**:28  
          inet addr:192.168.1.61  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::**:****:****:***/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9857924 (9.8 MB)  TX bytes:73662469 (73.6 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1556 (1.5 KB)  TX bytes:1556 (1.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:207.207.60.65  P-t-P:192.168.35.47  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:4385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4852491 (4.8 MB)  TX bytes:250985 (250.9 KB)


I know, eth0 is available and unconnected, but I am not too savvy when it comes to setting up multiple Ethernet links in Linux, and I've spent 4 hours trying to make that work.

Can anyone help? If it works with iptables, great. If it works with some sort of split tunnel or split access, fine. If someone can get me thru this using eth0 and eth1 together, awesome.

---

### Post by VAvenger on 2010-10-29
We came up with a solution. We used the dual NIC of my box, 1 port going to .60 and 1 port going to .61.

Created an empty IP table for all connections coming from the gateway to go thru .60 (eth0), everything else thru .61 (eth1) which default routes thru the VPN already.

Not the most elegant solution but it WORKS!

---

### Post by Sultore on 2010-11-10
Hey I wanted to say thanks for posting a follow up. I'm in a similar situation and your 'think outside the box' solution helped me find my own.

Thanks!

---

