---
title: "Problem with UDP packets ( simple nc test )"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by dlublink on 2010-07-09
Hello,

Imagine two computers. "a" runs Ubuntu 10.04 and "b" runs Ubuntu 8.04.

Computer a is running "nc 5000 -u -l".

Computer b runs "nc 192.168.1.5 5000 -u".

I enter text into computer b, when I hit enter I should see it on computer a.

For some reason I am not seeing it. I see the packets via "ngrep -qt -W byline port 5000", but I don't see them appear in nc.

I have the same issue with sending UDP packets in PHP, so it's not specific to nc. I used nc this example cause it's the easiest way to reproduce.

What's weird is that any 10.04 I have tried sending the UDP packet from works fine, and some other 8.04 machines work fine.

What could possible be installed on this computer that would cause the outgoing UDP packets to break like this ?

Here is an extract for tcpdump
```

11:53:52.596209 IP (tos 0x0, ttl 52, id 24185, offset 0, flags [DF], proto UDP (17), length 30)
    209.172.58.249.35400 > 76.10.183.248.5000: [udp sum ok] UDP, length 2
	0x0000:  0000 0200 0000 0000 0000 0000 0000 0800  ................
	0x0010:  4500 001e 5e79 4000 3411 d7ad d1ac 3af9  E...^y@.4.....:.
	0x0020:  4c0a b7f8 8a48 1388 000a ee56 630a       L....H.....Vc.
11:53:53.506550 IP (tos 0x0, ttl 52, id 50343, offset 0, flags [DF], proto UDP (17), length 30)
    209.172.58.253.59251 > 76.10.183.248.5000: [udp sum ok] UDP, length 2
	0x0000:  0000 0200 0000 0000 0000 0000 0000 0800  ................
	0x0010:  4500 001e c4a7 4000 3411 717b d1ac 3afd  E.....@.4.q{..:.
	0x0020:  4c0a b7f8 e773 1388 000a 9127 630a       L....s.....'c.



```


The first of the two packets is not seen by nc, the second is. The only difference I can see is the source port and the source IP.

Why would this not work ??

Please help.

David

---

