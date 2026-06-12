---
title: "Speed in home network; wired and wireless"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by pohamala on 2011-06-14
[FONT=Fixedsys]Hello,

I have some interesting results in my home network which I would like to understand better. It is about decent wired performance vs slow/moderate wireless performance.

The network configuration is following - see attachment:

So - servers and and boxes are physically connected, 2 1G routers having 1G wired connections and the last ap in chain behind 100Mbits eth. 

Now, when I run "iperf" between servers and can get decent 800Mbits, more or less what I expected.

If I do the same on wireless linux Ub1004/win-xp/win-7 clients (not shown in figure), regardless of wireless being g 54M or n 300M, I can get with iperf between 10-20Mbits only. This is from any client towards any server. File copying between server and an average client shows 3MBytes/s max.

What I can conclude is that the 804 and 1004 distros on servers are behaving similarly and I don't suspect any specific issue there. The server1 has ipv6 disabled, the server2 is as "out from the box". Something in the configuration in the network is throttling the speed so that I can't get benefits of 802.11n standard. I was expecting something in range of 100-150Mbits over wireless as ciphering obviously reduces some bandwidth.

What is your experience and judgment? Are there any known configuration options I could try to get the network performance seen from clients up? Or is the wireless on its edge and the only option get boost for clients is to connect them physically onto the network?

Br Pekka[/FONT]

---

### Post by pohamala on 2011-06-16
Ok, continuing the investigation. I took scanning of the channels, see the 1st attachment.
Then, using my desk-top pc, having dwa-547 802.11n 2.4GHz adapter, I one by one joined the three access points I have. Kippola2 is 54Mb whereas Kippola3 and 4 are 300Mb stations. But, the highest throughput was achieved with 54Mb station transfer rate being 20Mb/s and the 300Mb stations gave only 14Mb/s. Even more odd, the signal quality seen from desk-top driver sw seems to be ok and reports full 54 or 300Mb. The desk-top is win7/ubuntu1004 dual-boot and so far I haven't seen big difference on the throughput between OS's.
So, this points quite strongly towards 802.11n connections being somehow faulty. Maybe it doesn't have any connection to ubuntu at all but it is generic wireless problem. Does anyone know any good 802.11n troubleshooting and optimization guide?

---

