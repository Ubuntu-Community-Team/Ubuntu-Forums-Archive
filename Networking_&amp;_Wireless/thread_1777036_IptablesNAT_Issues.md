---
title: "Iptables/NAT Issues"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by jongd1i on 2011-06-07
Ok hoping someone might be able to help me out on this issue I have. First of all I will just make it clear my knowledge of Unix/Ubuntu is pretty limited so any help would be greatly appreciated. 
 
First of all I will try and explain what I am trying to acheive. 
 
I have an Ubuntu box that is currently on our Production environment with the IP address 10.167.8.200. On a seperate interface on this box I have a test lab environment that I am doing some work with an ASA (192.168.2.2). Basically I want to be able to connect from the Production environment on port 400 to the ASA box on 443. Underneath I have given screenshots of the routing table and interfaces. 
 
I was under the impression from a large amount of "googling" that I need to create an Iptable entry to make this work. I have created that entry but it does not seem to be accepted, but no errors rejecting it either. Connectivity directly from the Ubuntu machine works fine, I can SSH and HTTPS to it without a problem. 
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]andrew@gns3:~$ sudo iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 400 -j DNAT --to 192.168.2.2:443[/FONT][/SIZE][/COLOR]

[COLOR=#1f497d][SIZE=3][FONT=Calibri]andrew@gns3:~$ sudo iptables -L [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Chain INPUT (policy ACCEPT)[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]target prot opt source destination [/FONT][/SIZE][/COLOR]
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Chain FORWARD (policy ACCEPT)[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]target prot opt source destination [/FONT][/SIZE][/COLOR]
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Chain OUTPUT (policy ACCEPT)[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]target prot opt source destination [/FONT][/SIZE][/COLOR]

[COLOR=#1f497d][SIZE=3][FONT=Calibri]andrew@gns3:~$ ifconfig[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]eth0 Link encap:Ethernet HWaddr 00:0e:0c:6d:57:76 [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]inet addr:10.167.8.200 Bcast:10.167.8.255 Mask:255.255.255.128[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]inet6 addr: fe80::20e:cff:fe6d:5776/64 Scope:Link[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]RX packets:6204072 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]TX packets:11129543 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]collisions:0 txqueuelen:1000 [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]RX bytes:1530680100 (1.5 GB) TX bytes:2270287761 (2.2 GB)[/FONT][/SIZE][/COLOR]
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]eth1 Link encap:Ethernet HWaddr 00:0e:0c:6d:57:74 [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]inet addr:192.168.1.1 Bcast:192.168.1.255 Mask:255.255.255.0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]inet6 addr: fe80::20e:cff:fe6d:5774/64 Scope:Link[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]RX packets:1966 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]TX packets:3253 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]collisions:3 txqueuelen:1000 [/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]RX bytes:349933 (349.9 KB) TX bytes:525958 (525.9 KB)[/FONT][/SIZE][/COLOR]
 
[COLOR=#1f497d][SIZE=3][FONT=Calibri]andrew@gns3:~$ route[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Kernel IP routing table[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]Destination Gateway Genmask Flags Metric Ref Use Iface[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]10.167.8.128 * 255.255.255.128 U 0 0 0 eth0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]192.168.1.0 * 255.255.255.0 U 0 0 0 eth1[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]link-local * 255.255.0.0 U 1000 0 0 eth0[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]192.168.0.0 192.168.1.2 255.255.0.0 UG 0 0 0 eth1[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]default 10.167.8.254 0.0.0.0 UG 100 0 0 eth0[/FONT][/SIZE][/COLOR]

[COLOR=#1f497d][SIZE=3][FONT=Calibri]andrew@gns3:~$ ping 192.168.2.2[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]64 bytes from 192.168.2.2: icmp_seq=1 ttl=254 time=4.53 ms[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]64 bytes from 192.168.2.2: icmp_seq=2 ttl=254 time=0.976 ms[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]64 bytes from 192.168.2.2: icmp_seq=3 ttl=254 time=0.973 ms[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]^C[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]--- 192.168.2.2 ping statistics ---[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]3 packets transmitted, 3 received, 0% packet loss, time 2003ms[/FONT][/SIZE][/COLOR]
[COLOR=#1f497d][SIZE=3][FONT=Calibri]rtt min/avg/max/mdev = 0.973/2.159/4.530/1.676 ms[/FONT][/SIZE][/COLOR]

---

