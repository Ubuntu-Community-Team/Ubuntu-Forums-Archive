---
title: "LAN stopped working, but wlan still works"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-01-14
I have a small home network set up using wireless connection. I had everything set up nicely, and all the computers (one XP and three Ubuntu/XP dual booting) were able to see and communicate with each other over the network. File sharing was working well, although kind of slow. 

However, about a week ago, two of my dual booting machines were no longer able to access the network. They could both still access the internet, but file sharing didn't work. None of the other computers could see them on the network either - regardless of what OS was used. 

The hostnames of the computers are loltop, lolbox, Leodatorn, and Nina. The two first are the ones that have no access to the network anymore.

How do I find out what the problem is, and more importantly, how do I fix it? 

I don't know if it's relevant or not, but here's the output of ifconfig.

```
nevon@loltop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:80:65:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2023048681 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3606085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3606085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:402236686 (402.2 MB)  TX bytes:402236686 (402.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:47:3b:75  
          inet addr:192.168.55.101  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe47:3b75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26056992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26552768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17784690 (17.7 MB)  TX bytes:816140599 (816.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-47-3B-75-62-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by puppywhacker on 2009-01-14
your eth0 does not have an ip-address
your eth0 has rx dropped:2023048681

windows file sharing has it's own habbits, you don't need to see the computers to access them.

In the location bar of nautilus you could directly access the computers like this
smb://192.168.55.101/

or in the windows explorer like this
\\192.168.55.101\

Goodluck

---

### Post by Iowan on 2009-01-14
I haven't closely followed the evolution of Network Manager.  A version or two ago, NM wouldn't enable more than one interface - meaning you had to choose between wired or wireless.  You could still force the issue by configuring addresses in /etc/network/interfaces.  I've seen a few threads lately with both active, but maybe they were all having problems...

---

### Post by Nevon on 2009-01-14
I'm only using the wlan though. Also, it's not just Ubuntu&#8592;&#8594;Windows that doesn't work. Printer sharing and Ubuntu&#8592;&#8594;Ubuntu doesn't work either. smb://IP-ADDRESS works, but I would really prefer to be able to do it directly in nautilus... It's also quite bothersome since the rest of my family needs to be able to access my computer over the network, yet they can't see it. Plus, we're sharing a printer that's hooked up to my computer, yet with the network in this state, they can't access it.

---

### Post by Nevon on 2009-01-15
After some further investigation, it seems that Ubuntu &#8592;&#8594; Ubuntu file and printer sharing works. However, file- and printer sharing Ubuntu &#8592;&#8594; Windows does not, unless you goto smb://IP-ADDRESS of the computer you want to access, there's no nautilus integration. smb://hostname doesn't work.

This is really quite annoying. Any idea how to fix it?

EDIT: Sorry about that. Ubuntu &#8592;&#8594; Ubuntu file- and printer sharing DOES NOT work.

---

### Post by puppywhacker on 2009-01-15
The easiest is to connect to the shares in nautilus and than make a bookmark out of them.

It works better than to rely on windows name resolving. netbios naming is quiet unreliable. you could add the netbios-name to /etc/lmhosts, which works similar to normal /etc/hosts resolving. otherwise you probably end up troubleshooting which computer is the masterbrowser and trying to make NMB work again. I would keep it simple and focus on the things that work.

Goodluck

---

### Post by Nevon on 2009-01-15
> **puppywhacker said:**
> The easiest is to connect to the shares in nautilus and than make a bookmark out of them.

The computers are given their IP-addresses via DHCP, so a bookmark wouldn't work that great since I can't connect via hostname. Also, Ubuntu &#8592;&#8594; Ubuntu file- and printer sharing doesn't work even when trying to connect via IP. I can only access Windows shares like that. The next problem is that even if accessing the shares via IP works for me, my family is not very technical. They just want to be able to print their documents just like they always have, which used to work fine before this whole mess started. I really don't understand why it just stopped working all of a sudden, for no apparent reason. It was working great from the beginning.

---

