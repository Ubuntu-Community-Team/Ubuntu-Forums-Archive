---
title: "Having trouble connecting to a MAC-address based network"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by infm on 2009-02-06
I have a Lenovo Thinkpad W500, running Ubuntu 8.10, with the following wireless adapter

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

and I am having trouble connecting to a school wireless network based on MAC-address identification.
I have already checked everything I could think of (which is not much).

I was having trouble connecting to any wireless network, so I used [this]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/") guide to get my wireless card to work, because it just wasn't showing up on ifconfig or iwconfig

Anyway, I'm fairly new to Linux and Ubuntu, so I was wondering if there was anything that could be stopping me from connecting to my school network.

---

### Post by BrandonBan6 on 2009-02-06
Hi infm,

Welcome to Ubuntu and Linux...

Can you tell us a little more specific information about the troubles you are having. Can you see the wireless connection? Does it connect and not give an IP address? What happens when you try to connect to your school's network?

---

### Post by infm on 2009-02-06
> **BrandonBan6 said:**
> Hi infm,

Welcome to Ubuntu and Linux...

Can you tell us a little more specific information about the troubles you are having. Can you see the wireless connection? Does it connect and not give an IP address? What happens when you try to connect to your school's network?

Basically, from what the IT guy said, I'm trying to connect, and everything is set up just fine, but for some reason, I'm getting blocked.
He says the problem is on my end, but I'm not too sure since I don't have a firewall or anything that could be blocking my connection, unless the driver package in the guide I linked to earlier had a firewall of some sort.

---

### Post by BrandonBan6 on 2009-02-06
Hmm, that is still hard to tell. 

Can you paste a copy of your ifconfig list?
In terminal type ifconfig.

---

### Post by Sub101 on 2009-02-06
Is the school wireless restricting access based on MAC addresses?

If so, and you know your wireless works correctly, I would think it would be on the other end and that you have not been added to the list MAC list yet.

---

### Post by infm on 2009-02-06
> **BrandonBan6 said:**
> Hmm, that is still hard to tell. 

Can you paste a copy of your ifconfig list?
In terminal type ifconfig.

```
eth0      Link encap:Ethernet  HWaddr 00:21:86:a0:b8:dd  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:86ff:fea0:b8dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:985499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1003338591 (1.0 GB)  TX bytes:62576021 (62.5 MB)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1376 (1.3 KB)  TX bytes:1376 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:af:38:26  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:feaf:3826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146748 (146.7 KB)  TX bytes:5812 (5.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-AF-38-26-38-32-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by infm on 2009-02-06
> **Sub101 said:**
> Is the school wireless restricting access based on MAC addresses?

If so, and you know your wireless works correctly, I would think it would be on the other end and that you have not been added to the list MAC list yet.

Yes, basically you submit your MAC address to get added to the allowed list of computers.

The IT guy assures me that everything is working perfectly on his end.

---

### Post by infm on 2009-02-07
Shameless bump.
I really need this issue resolved :(

---

### Post by Sub101 on 2009-02-07
Ok, based on your ifconfig I think your card should work fine, but just to confirm, can you connect to other wireless networks?

And what security does the network use?

---

### Post by infm on 2009-02-07
> **Sub101 said:**
> Ok, based on your ifconfig I think your card should work fine, but just to confirm, can you connect to other wireless networks?

And what security does the network use?

Yes, I can connect to other networks.
They didn't tell me, but from what I gathered, they just use the allow list and some other sort of anti-vius type of protection system.

---

### Post by NoobBiscUiT on 2009-02-07
So they have some kind of VPN or MAC address filtering set up on their network?

and you have registered the MAC w/ them if so i assume.

Is there a way you can change your MAC address?
i know on some distros it's possible, also would uninstalling the card and re installing it help?


Is it possible that the card you are using, is incompatible w/ the encryption/authentication method on the network you are trying to connect to?

---

