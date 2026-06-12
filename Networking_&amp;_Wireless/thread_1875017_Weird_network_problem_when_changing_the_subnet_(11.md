---
title: "Weird network problem when changing the subnet (11.10)"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by kai-berlin on 2011-11-04
Hi everyone,

After upgrading to Ubuntu 11.10 I have a weird network problem. Here the setup:

I have a notebook and use it mostly at two locations (home / office). In my office we use a 10.0.0.0/16 subnet and at home if have a 10.4.0.0/24 subnet (the subnets are connect over a VPN BTW). When I start my notebook at one location the network is working perfectly as expected. But when I put my notebook to standby and go to the other location I get very weird behavior after waking up again: 

* If I go from home to work, after waking up, I can ping every computer in this subnet but I can't reach the "10.0.0.1" (what is the standard gateway here)
* If I go from the office to home I could ping every computer in the subnet (also the standard gateway what is 10.4.0.2 here), but I can't reach external sites in the Internet. 

After rebooting everything is fine again on both locations (until I go to the other one of course). The weird part is, that everything looks fine, after changing the location. It gets a new IP-address, the routing table is set correctly and I even tried to clear the arp-cache. But the network just works partly. 

Any ideas are highly appreciated. ;-)

Regards,
Kai

---

### Post by jonobr on 2011-11-04
It almost sounds like two different problems,

the one in work where you can puing everything in the subnet but not the gateway, the only way you can troubleshoot that it to wireshark/tcpdump the response from the gateway to see whats going wrong in the response.

When going back home can you ping internet addresses via IP?
this may clarify if its a dns updating issue which it sounds like it may be

---

### Post by kai-berlin on 2011-11-04
Thanks for your answer and yes, it sounds like two problems, but I still think it's one. OK, let's see who is right. :-) Wireshark is actually a good idea. Here what I get when I try a ping like "ping www.heise.de" (I am at home now):

```

11    4.764529    10.4.0.46    10.4.0.1    DNS    72    Standard query A www.heise.de
12    4.770714    10.4.0.1    10.4.0.46    DNS    230    Standard query response A 193.99.144.85

```And that's it. No more packets regarding the ping. The ping is showing something like:

```

PING www.heise.de (193.99.144.85) 56(84) bytes of data.
From 10.4.0.46 icmp_seq=1 Destination Host Unreachable

```(10.4.0.46 is my IP-address) 
So DNS is working and it's trying the IP-address. The routing table looks like this:

```

0.0.0.0         10.4.0.2        0.0.0.0         UG    0      0        0 wlan0
10.4.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.16.44.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.135.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8

```But what is interesting are the packets that are coming all the time:

```

13    4.774314    IntelCor_08:d7:a4    Broadcast    ARP    42    Who has 10.0.0.254?  Tell 10.4.0.46

```10.0.0.254 is the address of the Internet router in my office (I am at home). As I said, the standard gateway is 10.0.0.1. But it's only handling some VPN connections and forwarding all other packets to the router (.254). Maybe two more details:

* I have a Lenovo T410
* In my office I am using a cable ethernet connection and at home a WiFi. 

OK, that's it so far. The problem is, the next test I could do when I am going back into the office. And that's on Monday. :-)

-Kai

---

### Post by jonobr on 2011-11-04
So from the information your giving the arp request going out seems to think its still believesd that in order to route a packet it needs to pass it to 254 which is in your office.
Looking at your routes it believes the gateway is the .2 which is correct.

SOmething is retaining old info, I dont know what

---

### Post by kai-berlin on 2011-11-07
Back in my office, same problem. Here what I figured out:

A ping to 10.0.0.1 doesn't work and gives no packages in wireshark. A ping to a named host doesn't work (DNS is not working). But a ping to an IP-address works and gives these packages:

```

7    2.287447    10.0.2.88    8.8.8.8    ICMP    98    Echo (ping) request  id=0x2d96, seq=1/256, ttl=64
8    2.287703    10.0.0.1    10.0.2.88    ICMP    126    Redirect             (Redirect for host)
14    3.315377    8.8.8.8    10.0.2.88    ICMP    98    Echo (ping) reply    id=0x2d96, seq=2/512, ttl=55
15    3.996048    Wistron_f3:b9:b7    Broadcast    ARP    42    Who has 10.4.0.1?  Tell 10.0.2.88

```The redirect is a redirect to 10.0.0.254 (Internet router). Interesting, 10.0.0.1 is responding here. And here I have these "Who has 10.4.0.1" entries. Here is my arp table:

```

Address                  HWtype  HWaddress           Flags Mask            Iface
10.4.0.1                         (incomplete)                              eth0
10.4.0.1                         (incomplete)                              wlan0
10.0.1.245               ether   00:30:05:95:73:8a   C                     eth0
10.0.0.1                 ether   00:e0:81:32:44:f4   C                     eth0
10.0.0.254               ether   00:0d:b9:22:17:90   C                     eth0
Entries: 5      Skipped: 0      Found: 5

```I tried to delete the 10.4.0.1 entry, but it doesn't work. I look a little bit further and I figured out how to display the kernel's routing cache. The interesting part is, that there is a line:

```

Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface
10.0.2.88       10.0.0.1        10.4.0.1              0      0        0 eth0

```This Might be the reason. I wasn't able to clear this cache so I can't say it for sure. Meanwhile I figured out how to clear it and I will try it at home today. But if this is the reason, the question is, why it is not done automatically when changing the IP-address?

---

### Post by kai-berlin on 2011-11-09
OK, I tried it, but flushing the kernel routing cache doesn't help. After it's cleared, it is created in the same wrong way it was. I am sorry to say this, but the upgrade to 11.10 was a big mistake... I guess I will go back one version or give MintLinux a try.

---

