---
title: "Setting up static ip and port forwarding"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by which ones pink on 2009-03-31
Hi guys, I've searched around a bunch to figure out how to forward ports, but I'm still really a noob at this.  I'm using Intrepid, and I mostly only need this for Bittorrent clients.  Could someone give me step by step instructions for this?

My router is a Linksys WRT54G2.

Ifconfig:

```
ath0      Link encap:Ethernet  HWaddr 00:16:e3:75:d6:90  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe75:d690/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61647774 (61.6 MB)  TX bytes:42912185 (42.9 MB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:82:25:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6571 (6.5 KB)  TX bytes:6571 (6.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-75-D6-90-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339638 errors:0 dropped:0 overruns:0 frame:302216
          TX packets:93976 errors:34 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:97914720 (97.9 MB)  TX bytes:46545895 (46.5 MB)
          Interrupt:22 

```
/etc/network/interfaces:

```
auto lo
iface lo inet loopback

```
It seems to me that there's not enough information in this file, from what I've seen on the forums.

Thanks for your time.

---

### Post by bgerlich on 2009-03-31
You'll be forwarding ports on your router, not the Ubuntu machine. On most routers you can setup automatic port forwarding (Upnp), most Bittorrent clients support it. Transmission does, as does Vuze and Deluge.

---

### Post by which ones pink on 2009-03-31
> **bgerlich said:**
> You'll be forwarding ports on your router, not the Ubuntu machine. On most routers you can setup automatic port forwarding (Upnp), most Bittorrent clients support it. Transmission does, as does Vuze and Deluge.

I know that you do it from the router, but I still need help :( The thing is the only torrents that aren't working are from Demonoid.com (where I get most of my stuff, actually), and the torrents are labeled as "private" in Vuze.  A guy on the Demonoid forms who uses Ubuntu said they work fine for him, and I need to forward my ports.  So I'm trying that, because I really don't want to have to boot XP every time I want something from Demonoid.

---

### Post by bgerlich on 2009-03-31
Tools > Option > Plugins > UPnP - that's where you turn automatic port forwarding in Vuze.

On your router I don't know, the manual says it works with Upnp, but you will have to locate the option to turn on Upnp - it could be on already if it works in Windows ...

---

### Post by which ones pink on 2009-03-31
I'm not sure if Upnp is enabled on the router.  I'll check when I get home, on my phone right now.

---

### Post by which ones pink on 2009-03-31
Alright so Upnp is enabled on the router, Vuze, and Deluge.  Demonoid torrents still just sit there, doing absolutely nothing, no matter how good the seed/leech ratio is (one of the torrents I'm trying has 300+ seeds and 4 leechers).

So, how can I set up a static IP?

---

### Post by sidcypher on 2009-04-17
kinda a dumb question, but i assume you have logged onto demonoid in firefox..doesn't that site set a cookie, so it can track your ratio? 

Cause once I had my desktop logged into there, and logged from my laptop while on trip, and it kicked my ratio tracking off the desktop...that was sad...i had to seed FOREVER..lol

so i would assume it verifies you ident somehow with the cookie through the tracker, idk

i could be WAY off, but my 2 cents

---

