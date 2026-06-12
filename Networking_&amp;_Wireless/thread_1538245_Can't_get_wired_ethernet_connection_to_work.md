---
title: "Can't get wired ethernet connection to work"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by OzuYatamutsu on 2010-07-24
Hi, I have a HP Mini running Ubuntu Desktop 10.04, and I cannot get a wired connection to work. My network card is "Broadcom Corporation BCM4312 802.11b/g (rev 01)", and I have the restricted drivers for the card installed. Wireless works fine, though.

My /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Any help would be appreciated!

---

### Post by Iowan on 2010-07-25
Does either card work? 
Are they connected to different networks? 
(What are results of **ifconfig -a**?)

---

### Post by nathan.osborn1 on 2010-07-25
I was having the same issue....I figured out how to fix mine realyl easy I just selected auto connect for hard wired connections. I am sure you probaly already tried this but just htought I would drop the suggestion.

---

### Post by OzuYatamutsu on 2010-07-27
Hi, sorry it took so long to get back.

When I'm not connected to wireless but have a cable plugged in, ifconfig -a shows this:

eth0      Link encap:Ethernet  HWaddr 00:24:81:3c:30:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:88:f9:ed  
          inet6 addr: fe80::224:2bff:fe88:f9ed/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20053 errors:354 dropped:0 overruns:0 frame:161304
          TX packets:16659 errors:179 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18499828 (18.4 MB)  TX bytes:2338017 (2.3 MB)
          Interrupt:16 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:81:3c:30:9d  
          inet addr:169.254.6.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3849845 (3.8 MB)  TX bytes:3849845 (3.8 MB)

When you say "either card", are you talking about separate wireless and ethernet cards? Because it only shows the one Broadcom card...

nathan.osborn1: I'm not sure what you mean, where did you set "auto connect"? I'm kind of new at this :(

---

### Post by OzuYatamutsu on 2010-07-27
Nevermind, I solved it from the steps described here: 
[http://ubuntuforums.org/showthread.php?p=8378695](http://ubuntuforums.org/showthread.php?p=8378695)

Thanks for your concern!

---

