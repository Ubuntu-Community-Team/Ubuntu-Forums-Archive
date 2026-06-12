---
title: "Constant, frequent, brief disconnections."
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by Orgullomoore on 2006-06-28
I am using Ubuntu 6.06 LTS/Dapper Drake on my desktop computer. 

I connect through an ethernet port to my Linksys Wireless G 2.4GHZ broadband router, which is connected to my Cable modem. The ISP is Road Runner. 

Ubuntu has no problem detecting the connection nor connecting to the Internet through it, it only has a problem staying connected. Every once in a while (the "while" can range from 30 seconds to an hour), the connection is killed and immediately brought back up. The router continues to show connectivity and if I'm browsing the Internet, for example, I don't even notice it, because the connection is immediately reestablished. 

For applications that require a constant connection, however, I have to manually reestablish the connection. 

Examples:
*IRC
*Music streaming
*Instant messaging (GAIM)

I've used this same connection under Windows XP and Debian Sid without this problem. 

I thought it might be the NIC, so I bought a new one. Problem persists. 

I will post my ifconfig output below. 

```
eth0      Link encap:Ethernet  HWaddr 00:12:17:56:74:71
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe56:7471/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:212075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:182402160 (173.9 MiB)  TX bytes:16817597 (16.0 MiB)
          Interrupt:169 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
```

---

### Post by Orgullomoore on 2006-06-28
Hmm...no one responds. Just to throw a guess out there, maybe this will help:

Could it be that I'm using up too much bandwidth and because of this the IRC connection is forced to close? I constantly run several bots for Wikipedia that take up a whole lot of bandwidth. 

How can I test this?

---

### Post by Orgullomoore on 2006-06-28
Update: This forum was of no help :rolleyes:. That's okay, maybe next time. The problem was indeed that I was running 8 bots that used up a lot of bandwidth and when it took up too much bandwidth, there wasn't enough left to even access IRC. 

Okay, lesson learned. Now some one can learn from my mistake if they search this forum. I either need to pay for a bigger connection or stop using up so much bandwidth.

---

### Post by zxee on 2006-06-29
[QUOTE=Orgullomoore]Update: This forum was of no help :rolleyes:. That's okay, maybe next time. The problem was indeed that I was running 8 bots that used up a lot of bandwidth and when it took up too much bandwidth, there wasn't enough left to even access IRC. 

Okay, lesson learned. Now some one can learn from my mistake if they search this forum. I either need to pay for a bigger connection or stop using up so much bandwidth.[/QUOTE]

I'm curious though if the above is the reason for disconnects then why as you noted here:
> I've used this same connection under Windows XP and Debian Sid without this problem.
 did you not experiance it with the above mentioned OSes? There is a thread here about servers that use microsoft protocol not working well with the latest linux kernel.
And I like being told I wear a tinfold hat O:)

---

### Post by Orgullomoore on 2006-06-29
My guess is that I just topped it off with this last bot that I wrote (which is quite a bandwidth hog). I used Debian Sid exclusively to test my connection--to see if it was a bad driver that Ubuntu had installed, if it was my ISP, or why I was being disconnected; I wasn't running all the bots. 

I used Windows to run 7 of the bots, I guess my connection just couldn't handle any more. 

Anyway, I'm gonna have the programs run on a different server so I can have my bandwidth all to myself :)

---

