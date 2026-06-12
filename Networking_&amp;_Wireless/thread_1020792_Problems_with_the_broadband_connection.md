---
title: "Problems with the broadband connection"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Tarif Ezaz on 2008-12-24
I have been using Ubuntu 8.04 for six months. Throughout this period, I have a broadband internet connection. Me and my internet partner share the same ip address with two different MAC addresses. What happens is that when both of us try to log in to the pc, the connection becomes too slow and one of us have to step down. But the problem that I've been facing occurred a few days ago when I was surfing and my partner came in. I came out as usual. But when I tried to log in the next time, the connection was not working. Basically this problem solves by himself after sometime. But this time this is not the case. I configured the connection again, but I doesn't seem to work. By the way, I can use the internet in this same machine from the windows operating system.

A few days ago I updated to Ubuntu 8.04.1 from the Update manager.

I ran an ipconfig from the terminal and here's the output:

 Link encap:Ethernet  HWaddr 00:16:76:cf:74:d9  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fecf:74d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:875015 (854.5 KB)  TX bytes:57226 (55.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:81000 (79.1 KB)  TX bytes:81000 (79.1 KB)


Can anyone please help!

Regards
tarif

---

### Post by cabbiinc on 2008-12-24
Have you tried changing the IP address to your Ubuntu machine?

Click the network icon next to the clock.
Manual configuration.
Unlock > enter password
click the connection and then properties button
In the IP address just change the last digit to something that's not being used. Note what the number originally is in case that doesn't work.

---

### Post by Tarif Ezaz on 2008-12-24
Thanks. I have tried all the combination, but it didn't work :(
any more ideas?

Regards
tarif

---

### Post by cabbiinc on 2008-12-24
> **Tarif Ezaz said:**
> Thanks. I have tried all the combination, but it didn't work :(
any more ideas?

Regards
tarif

If you know the IP address of your broadband modem you can put that in your browser in place of a URL and hit enter. I did that and was able to change settings in the modem. Not sure if it would help though but it might be worth a try.

How are you connected to the modem?

---

### Post by Tarif Ezaz on 2008-12-24
Is there any way to know the IP of my broadband modem? Cause I do not know it. Could you please let me know how?

Regards
tarif

---

### Post by cabbiinc on 2008-12-24
> **Tarif Ezaz said:**
> Is there any way to know the IP of my broadband modem? Cause I do not know it. Could you please let me know how?

Regards
tarif

I haven't had Ubuntu long enough to know what programs do this so I will give you a windows link, you did say you have Windows didn't you. [http://www.majorgeeks.com/PingEasy_d5696.html](http://www.majorgeeks.com/PingEasy_d5696.html) Its a small program, run it. The actual program that comes up is PingTest.exe.

In pingtest there's 2 tabs at the top. Ping and IP Scanner. Click IP Scanner.
For the IP range put 192.168.1.0 to 192.168.1.255.
It should run a scan and give you one or two hits off that range, and if your lucky it will tell you what those hits go to. You can probably decifer which IP address is what once you have something to work with.

---

### Post by Tarif Ezaz on 2008-12-25
I'm not making any progress :(

---

