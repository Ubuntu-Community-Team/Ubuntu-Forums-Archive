---
title: "No Internet"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by fatsheep on 2010-06-05
So I'm having a weird problem here...  I have had Ubuntu set up on my Mom's computer for 2 years and this is the first time I'm having a major problem with it: it can't connect to the internet.  I can't see any reason why and another computer on my home network can connect just fine (we're talking about a wired connection here).  

I haven't diagnosed something like this in quite some time so I thought I'd ask for some help here.  Here's some commands I ran: 

> anne@anne-desktop:~$ ping 192.168.0.1     <== this is the router
connect: Network is unreachable

anne@anne-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:86:d5:f2  
          inet6 addr: fe80::2e0:4dff:fe86:d5f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22656 (22.6 KB)  TX bytes:3952 (3.9 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


As you can see, I can't even successfully ping the router that I am directly connected to. :(  Not sure what that's about... 

 Any help would be greatly appreciated.  Just FYI I won't have access to the computer till next weekend so I may take till then to provide more information if it requires the computer.  Thanks,

Jesse

---

### Post by felixtheratruns on 2010-06-05
1. Can you ping loopback?
2. Have you verified that the card works fine in another machine?
3. show us "sudo iptables -L -n" 
4. Are you really a fatsheep? because I'm a fat ox

5. Do you also have no network icon?

6. I'm a semi newb, so I might be able to help you that much

---

### Post by Iowan on 2010-06-05
From a terminal, try **sudo dhclient eth0**. Right now, eth0 has no IP address.

Also, unlikely as it might seem... check to verify that networking isn't disabled (make sure it's enabled).

---

