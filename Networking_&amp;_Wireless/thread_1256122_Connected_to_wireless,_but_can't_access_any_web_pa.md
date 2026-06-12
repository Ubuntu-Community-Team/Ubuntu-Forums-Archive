---
title: "Connected to wireless, but can't access any web pages"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by funqshun on 2009-09-02
hello, i'm on jaunty and i have the following problem:

i can connect to my wireless connection, but i cannot access any web pages.
firefox 3.0.1.0 gives:

Addres not found
Page Load Error

ifconfig gives:

eth1
Link encap:Ethernet HWaddr 00:0e:35:2d:a3:6d
inet addr: 192.168.0.142
Bcast: 192.168.0.255
Mask: 255.255.255.0
inet6 addr: fe80:20e:35ff:fe2d:a36d/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
RX packets: 212 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 211 errors: 0 dropped: 5 overruns: 0 carrier: 0
collisions:0 txqueuel en: 1000
RX bytes: 29868 (29.8KB) TX bytes: 82262 (82.2KB)
Interrupt: 11 Base address: 0xe000 Memory: d0200000- d0200fff


My /etc/network/interfaces file reads:

auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp

Help!
Posting from a temporary connection.

---

### Post by jnorthr on 2009-09-02
suggest you try using another browser than firefox as it often needs a config setting to "talk" to your network. Can you use any of the administration features to  update your system ? If so it may just be firefox, if not then you may not REALLY be connected.

---

### Post by funqshun on 2009-09-02
i've tried opera and kazehakase to no avail.

pinging google.com shows 'unknown host google.com'.

clearly i dont have a route to the net. my wireless is password-free. what am i doing wrong?

---

### Post by decahedron on 2009-09-12
Hello All,

I am able to connect to my network at home and use internet (firefox) with no problems.  When I go to school my computer connects to the network but firefox can not find any web addresses.  What settings might I need to make in order for firefox to find the network.  

Thanks

---

### Post by hockeytux on 2009-09-12
I had the same problem with a new comp but I fixed it by setting up the connection again. The default settings were no good in my case.

---

### Post by eagle416 on 2009-09-21
> **decahedron said:**
> Hello All,

I am able to connect to my network at home and use internet (firefox) with no problems.  When I go to school my computer connects to the network but firefox can not find any web addresses.  What settings might I need to make in order for firefox to find the network.  

Thanks

That is basically my situation as well. I can ping websites and get a response. The IT guy said that linux users were having trouble with it, but I'm not exactly sure why. I could connect to the network last year (on Hardy) and it worked fine.

---

### Post by _problem_ on 2009-09-26
Same thing happening here, i was able to connect to the internet before, then i started playing halo multiplayer online and now i can't view webpages. i tried everything and it said the problem couldn't be repaired automatically, none of my huawei 3 wireless broadband connections work. but the strangest thing is that they all work on my other 2 laptops:confused:, i was starting to think somebody hacked me:confused: it also says that the network adapter is damaged

---

### Post by _problem_ on 2009-09-26
oh yeah and i can see no data is uploaded nor downloaded, but it says we are connected:confused:

---

### Post by shredder12 on 2009-09-26
Sometimes such issues arise due to enabled IPv6
you may try checking it ..
use this command 
```
lsmod | grep inet6
```

If a command line is returned then its probably not an ipv6 issue..
but it something is returned then you should disable it..

btw.. in both the cases. .. you may try disabling IPv6 for your browswer...
enter "about:config" in the URL bar 
and look for network.dns.disableIPv6

if it is set to false.. then double click it and change it to true..
see if you are able to open web pages now..

---

