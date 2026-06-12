---
title: "Another wired connection that cant connect."
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by all metro on 2009-01-21
I need some help. I have a dual boot system with XP and Ubuntu 8.10. I am setting up a static ip but I have run into a road block](*,)

I have set the network Manger up with all the same info that works for my XP mach. It says it is connected but Firefox won't load. When I try to ping other computers on the network it works fine but when I ping outside of the network I get 100% loss? 

I have tried "sudo nano /etc/network/interfaces" and put the info by hand, with no luck there. I even put the DNS in by hand still nothing. 

I am not a network pro by any means. I do have a few questions?
Would I need to assign a different IP for the Ubuntu OS since XP is using 10.0.0.102. And would I also have a different MAC add. or would it be the same as my XP address? 

Any help would be greatly appreciated.):P
Thanks Tim

---

### Post by Kebabman on 2009-01-21
Firstly, no you will not need a different IP address or MAC address the same information will work in windows and Linux.

This sounds to me like it might be a DNS issue can you try the following in a terminal and paste the results please :

nslookup google.com

and

ping 72.14.205.100

---

### Post by all metro on 2009-01-21
Thanks for the quick reply.
When I ping 72.14.205.100 I get "network is unreachable".
When I type nslookup google.com I get nothing. Just blank.

Thanks Tim

---

### Post by Kebabman on 2009-01-21
Oh, it's just clicked as to what this probably is.

Because you have set up all the information manually you need to add a default route. Type this in a terminal:

'route add default gw <address of your router>'

See if that works for you.

---

### Post by all metro on 2009-01-21
I get "SIOCADDRT: no such process" 
Not sure what that means.

Tim

---

### Post by all metro on 2009-01-21
question, gw would that be "gateway" ?
Do I need to add my gateway ip or my router ip ? 

Thanks for you help

---

### Post by sedawk on 2009-01-21
Run route without argument and post the output here ( and the output
of ifconfig without any arguments)

Assuming your router is 10.0.0.1 please first try this (again):

```

route add default gw 10.0.0.1 

```

and retry the tests posted above.

---

### Post by all metro on 2009-01-21
ext209@ubuntu:~$ route add default gw
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported




ext209@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:37:c0:62  
          inet addr:10.0.0.102  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe37:c062/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99585 (99.5 KB)  TX bytes:21899 (21.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15683 (15.6 KB)  TX bytes:15683 (15.6 KB)

---

### Post by all metro on 2009-01-21
That was it !!!!!!!!!!!!!!! YAHOOOOOOOOOOOOOOO
sudo route add default gw 10.0.0.254
I am now on this site with Ubuntu 

Thanks a TON guys

---

