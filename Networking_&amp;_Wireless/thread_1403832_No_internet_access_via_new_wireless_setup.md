---
title: "No internet access via new wireless setup"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by Slates on 2010-02-10
Running Ubuntu 9.10 Ive just got my wireless connection working (thanks to replies from other posts) after first having got the wired eth0 connection working.

With the wired connection I could SSH into my server through my firewall/router (via a forward). I can run up VNC, from there firefox, browse the web - all is well.

I have now setup the wireless connection, using a static IP, and I can likewise SSH into my server.  I can run up VNC. I can ping my router. I can log onto it via VNC. I can browse to my router. But I cant browse the internet.

But I cant ping google.com. The reason is there is no host lookup service. Nslookup eventually says no servers could be reached. 

So specifically, if I ping [www.google.com](www.google.com) Im told "unknown host".
If I do an NSlookup on it I get timeout, no servers could be reached.
However if I ping 66.102.11.104 I get responses. 

I see no relevant entries in my firewall log. 

Unfortunately I cant traceroute because the package isnt found - and of course I cant install it because I have no internet !

Strangely (to me at least !) if I then tunnel through SSH and browse the web, I have no problems. It works ? I know I am browsing through my SSH tunnel because whatsmyip gives the IP of my router at home, not where Ive SSHd in from. I can surf just fine.

Anyway, can someone please explain why I cant do host lookups any more (and this did work with my wired connection, but whether its related to my change to wireless, or static IPs or both I cant be sure - it certainly appeared to happen at the same time). And, more to the point, what I need to look for/do to rectify it ?

As a bonus Id be interested in why I can SSH and browse via tunnelling but not direct from my server (via VNC). Just for interests sake ! 

if config reports :

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:27:ae:17
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe27:ae17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2108727 (2.1 MB)  TX bytes:6834123 (6.8 MB)
 
my router is on 192.168.1.254.

---

### Post by Slates on 2010-02-10
There's so much great help on these forums ... Im trying my best to help myself as well !! On that topic, 

Im looking at the network config, although Im lacking the knowledge to know why I would be able to access the internet but not use name lookup, and after checking the static IP setup in the GUI where I set up wireless in the first place, I also notice that /etc/network/interfaces only had a loopback entry in it.

So I added this and restarted the network :
iface wlan0 inet static
address 192.168.1.69
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.254
broadcast 192.168.1.255

But this has made no difference. I must be barking up the wrong tree ?

---

