---
title: "New wubi 8.10 install - can't connect to network"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by prythin on 2009-03-21
I have a new wubi 8.10 install and seem to be having similar problem to other users - it has autodetected eth0, which claims I am connected to the wired network but when I open a browser, I find I am not connected.

I've tried manually adding my network connection which has the effect of disconnecting me altogether. I've also tried deleting the network settings and restarting, which worked for some users but has not worked for me.

I'm on an ADSL2+ connection on a Compaq Presario desktop machine, normally running Vista. Everything else about my install seems fine.

Output of sudo lshw -C network is as follows: 

prythin@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:d8:4c:8b  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3070 (3.0 KB)  TX bytes:2915 (2.9 KB)
          Interrupt:252 

prythin@ubuntu:~$ ifconfig pan0
pan0      Link encap:Ethernet  HWaddr be:01:21:0c:5e:96  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

prythin@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:01:21:0c:5e:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

If I do sudo dhclient eth0 I get a message about send_packet: message too long. (Unfortunately I can't give the exact message as I tried to dump this to a text file in windows but it didnt work). 

I've also tried adding 

auto eth0
iface eth0 inet dhcp 

to /etc/network/interfaces and restarting the network, which results in the same message about send_packet:message too long, and nothing connects. My /etc/network/interfaces had only auto eth0 before. 

I'd appreciate any help with this - I've never used ubuntu before and am somewhat rusty with linux networking.

cheers
prythin

---

### Post by prythin on 2009-03-21
Update - since rebooting this morning for some reason my network connection has suddenly decided to work. I'd rebooted a few times last night, so I'm really not sure why it wasnt working after the changes I documented above.

However, I think the fix may have been adding this to /etc/network/interfaces as my eth0 didn't seem to have been configured.

> **prythin said:**
> 
auto eth0
iface eth0 inet dhcp 

Are there known bugs for autodetection of dsl devices in 8.10?

---

