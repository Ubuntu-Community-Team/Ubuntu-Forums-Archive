---
title: "Problems with findsmb command after installing VMWare server."
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by SkarpHedinn on 2009-04-17
I've installed VMWare Server 2.0 (followed the default prompts in the installation process) and now I notice the findsmb command is resulting in only one result, despite having several active samba shares on my network. I'm not really sure where to begin troubleshooting this issue (I've only been working with ubuntu for 8 or so months now). I, therefore, apologize if this thread is in the wrong location and if I'm broadcasting my ignorance in it at an uncomfortable volume.

So then, it appears that when findsmb is looking on the wrong subnet for these shares. When I run ifconfig I get: 

eth0      Link encap:Ethernet  HWaddr 00:21:85:10:13:e5  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe10:13e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49679 (49.6 KB)  TX bytes:21133 (21.1 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44704 (44.7 KB)  TX bytes:44704 (44.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.84.1  Bcast:172.16.84.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.12.1  Bcast:172.16.12.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I'm presuming I want it to look on the 192.168.1.x range of subnet IPs to detect shares. Instead, when executing findsmb I get the following:

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
172.16.12.1     RAAM          +[WORKGROUP] [Unix] [Samba 3.2.3]


RAAM being the computer I'm running the command on. Now, I can manually connect to the shares just fine, but I'm curious as to why/how this has happened, and if I might be able to get findsmb back in my toolbox. Any advice?

My version of Ubuntu is Intrepid and I'm using VMWare Server 2.0.

Edit: I get the same results even when entering 'findsmb 192.168.1.255'

---

### Post by SkarpHedinn on 2009-04-18
I've now installed nbtscan and when inputting the desired IP range it does look like I'm getting at least some of the results back that I'm looking for.

Nevertheless, this is still kind of a pain, as when I open the "Places" menu and select "Network" the share I'm looking for still isn't displaying. Again, I can manually connect to the share, but for some reason I can't get it to appear for me in the list of available shares (as it had prior to installing VMWare Server). Any advice?

---

