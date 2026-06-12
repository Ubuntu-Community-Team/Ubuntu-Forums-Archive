---
title: "[SOLVED] Server with two NIC's"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2008-12-21
I have recently activated the second NIC for my Ubuntu 8.1 server.  Since activating the second card I have had nothing but problems.  First I find out that NW 0.7 is buggy and does not support static ip's very well at all.  I have now installed wicd to take NW's place and now for some reason which I do not understand, (probably just my thick head) I cannot access the machine on either card from the outside world.  No remote, no ssh, and no telnet.  However, I can successfully ping both NIC's with the ip address and one card with the domain name.  Also, I can get out from the machine to the outside world on a browser, update and synaptic.

Does anyone have any suggestions of how to diagnose the problem?

Any suggestions would be appreciated.

Ron

---

### Post by superprash2003 on 2008-12-21
post ifconfig output.. also has your ip changed .. have you port forwarded?? post output of sudo iptables -L

---

### Post by Iowan on 2008-12-21
Aforementioned information will help answer some of the following questions:
NW - Netware? (probably Net Manager)
Both cards are active? How (and/or to what) do they connect?
Both cards aren't in the same subnet?

---

### Post by quikone8 on 2008-12-21
Thanks both of you for the responses.  I will post the information sometime in the next 60 minutes, i need to get to the location where the machine resides.

Thanks again,

Ron

---

### Post by quikone8 on 2008-12-21
> **superprash2003 said:**
> post ifconfig output.. also has your ip changed .. have you port forwarded?? post output of sudo iptables -L

Following are the outputs requested.  I have not changed my ip, but I have added one.  eth0 was the only one at first, I recently added eth1 for a VM client.  I don't think I have done any port forwarding, although I will bridge one of the connections when I get the fiorst part fixed.

eth0      Link encap:Ethernet  HWaddr 00:11:43:ed:56:d7  
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:feed:56d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:11225204 (11.2 MB)  TX bytes:2801812 (2.8 MB)

eth1      Link encap:Ethernet  HWaddr 00:11:43:ed:56:d8  
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:feed:56d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3645538 (3.6 MB)  TX bytes:309273 (309.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6937444 (6.9 MB)  TX bytes:6937444 (6.9 MB)

vnet0     Link encap:Ethernet  HWaddr 22:9e:cc:0b:f0:1f  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::209e:ccff:fe0b:f01f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:143616 (143.6 KB)

ron@tolmarket:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Thanks again, 

Ron

---

### Post by quikone8 on 2008-12-21
> **Iowan said:**
> Aforementioned information will help answer some of the following questions:
NW - Netware? (probably Net Manager)
Both cards are active? How (and/or to what) do they connect?
Both cards aren't in the same subnet?

NW does = Network Manager
Both cards are active, see the output in the post above.
Both cards are on the same subnet, is that a problem?  One will be used for the main machine and the other for the VM client.

Thanks,

Ron

---

### Post by Iowan on 2008-12-21
Having both cards in same subnet will (probably) play havoc with routing - *might* be what's causing your problem (although I'm not familiar with VM requirements).  Try changing one (probably eth1) and see if things get better.

---

### Post by quikone8 on 2008-12-21
> **Iowan said:**
> Having both cards in same subnet will (probably) play havoc with routing - *might* be what's causing your problem (although I'm not familiar with VM requirements).  Try changing one (probably eth1) and see if things get better.

I know this is probably a very dumb question, but I won't learn unless I ask it, If I am being served say 192.168.1.0/255.255.255.0, can I change the subnet to  something else?

---

### Post by Iowan on 2008-12-22
You probably won't be issued 192.168.1.0 or 192.168.1.255 (as those are broadcast addresses)... but I realize that's just an example. You *can* change the subnet, but it probably won't work.  If you change the subnet (to say 255.255.255.248) that machine will be the only one there - no one else to communicate with - the router in particular. 
   Another potential problem for the VM client is that as a DHCP client, eth1 becomes a moving target. It should *probably* have a fixed address. (Did I mention I'm not familiar with VM?).  Fixed (static) addresses have their own problems on 8.10.  This [workaround]("http://ubuntuforums.org/showthread.php?t=974382") covers a few.

---

### Post by quikone8 on 2008-12-26
This problem was solved by rolling my system back to 8.04, I will go back to 8.10 and Network Manager when it is fixed and proven.  Now everything again.

---

