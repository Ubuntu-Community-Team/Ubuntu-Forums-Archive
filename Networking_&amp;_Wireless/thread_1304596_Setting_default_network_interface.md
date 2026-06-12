---
title: "Setting default network interface?"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by PHaLaNX on 2009-10-29
Hi,

I have one wifi adapter (wlan0) and a dsl modem (ppp0) connected to the pc. The problem is whenever I connect to a wifi network with internet access, all my internet connections are made using the wifi card.

I want it to use the wifi card only for it's own network (192.168.1.1/24 for example) addresses and use the dsl modem for every internet connection. 

I searched it a little bit but couldn't figure out how to do it because my settings look a little different. 

Any help would be appreciated...

Here is the ifconfig -a output:

```

eth0      Link encap:Ethernet  HWaddr XX-XX-XX-XX-XX-XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              
          Interrupt:16                                        

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                              
          RX bytes:626741 (626.7 KB)  TX bytes:626741 (626.7 KB) 

pan0      Link encap:Ethernet  HWaddr XX-XX-XX-XX-XX-XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                           
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XX.XX.XX.XX  P-t-P:XX.XX.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1     
          RX packets:14725 errors:0 dropped:0 overruns:0 frame:0         
          TX packets:16013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:14016625 (14.0 MB)  TX bytes:2109833 (2.1 MB)

tap0      Link encap:Ethernet  HWaddr XX-XX-XX-XX-XX-XX
          inet6 addr: XX-XX-XX-XX-XX-XX/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:15857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:14408591 (14.4 MB)  TX bytes:2497338 (2.4 MB)

wlan0     Link encap:UNSPEC  HWaddr XX-XX-XX-XX-XX-XX
          inet6 addr: XX-XX-XX-XX-XX-XX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25524608 (25.5 MB)  TX bytes:468 (468.0 B)
          Interrupt:19

```

ppp0 and tap0 are kinda like the same I think. Don't know about the pan0.

The /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

```

Thanks...

---

### Post by PHaLaNX on 2009-10-29
Anyone?

---

### Post by Iowan on 2009-10-29
Sounds like **route** needs some adjustment. Network Manager (dunno about Kubuntu... sorry) has an option to configure routes - or you can use the **route** command to add them. **man route** has more specifics, but you'd want 192.168.1.0/24 routed through wlan0 and the default route set to ppp0.
BTW, pan0 would be Personal Area Network (bluetooth).

---

### Post by PHaLaNX on 2009-11-01
Sorry for the late come back... 

Well I don't always know the wifi network's addresses, as it can be a different network all the time. I just don't want ubuntu to make an internet connection via wlan0 no matter which network it is. Like, I can have amsn open, and when I connect to a wifi point it auto connects to msn, which is something I don't want. 

And route table doesn't seem to be consistent, each interface just overwrite it when they become active.

---

### Post by PHaLaNX on 2009-11-01
Anyone knows about it?

---

### Post by PHaLaNX on 2009-11-05
Can anyone help? I can give more information if what I said isn't enough.

---

### Post by Iowan on 2009-11-05
Is wlan0 configured via Network Manager, or via */etc/network/interfaces*? Does **route** show a default gateway for wlan0?

---

### Post by PHaLaNX on 2009-11-05
I've never used network manager, I don't even have in my menus. I use iwconfig to connect to networks.

I also never edited /etc/network/interfaces and it's as I posted before. 

When I'm not connected to a wifi network, route -n gives this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
my_dsl_ip       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

and when I connect one it becomes:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
my_dsl_ip       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

And all the internet traffic goes via wlan0 (given the network it connects to has internet access).

---

### Post by jward3010 on 2009-11-05
I'm almost 100% sure that network-manager and possibly the use of iwconfig is just limited to using one connection, and I'm not sure how it picks. You'll have to set up the wlan and PPP connection in your interfaces file to do multiple connections (/etc/network/interfaces). How exactly this is done, I can't tell you unfortunately, I'll hope someone else will come in on this.

Someone might correct me of course, but I've seen this a lot throughout the forums and the answer has been "NM doesn't multiple connections yet, do it with interfaces".

---

### Post by Iowan on 2009-11-05
> **jward3010 said:**
> Someone might correct me of course, but I've seen this a lot throughout the forums and the answer has been "NM doesn't multiple connections yet, do it with interfaces".Until my Jaunty laptop started connecting to my home wired network AND the neighbor's wireless network (all apparently via NM) I'd have agreed that NM was "one manager, one interface". Now, I'm not so sure...

---

### Post by jward3010 on 2009-11-06
> **Iowan said:**
> Until my Jaunty laptop started connecting to my home wired network AND the neighbor's wireless network (all apparently via NM) I'd have agreed that NM was "one manager, one interface". Now, I'm not so sure...
I'm confused - whats which - are both the internet or just one internet and one purely local?

---

### Post by Iowan on 2009-11-06
> **jward3010 said:**
> I'm confused - whats which - are both the internet or just one internet and one purely local?I'm not having a problem, but the wired network has my other machines - also can connect to internet... so it could theoretically have internet access either/both ways. This is not how I'm used to having NM work, but I don't plan to complain.

---

### Post by jward3010 on 2009-11-07
You see, I think you're being tricked into thinking you're actually using your neighbours internet. It might be connected but it never sends packets that way, it always uses your wired network. And what you're saying makes sense to how nm works. When two connections are created it will always use the faster one - the wire.

Here's the test disconnect the internet on your network (wired) and see if it gets the internet through your neighbours gaff AND still connect to your local PC's. I don't think it will.

---

