---
title: "Low internet speed on ubuntu"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by balaji on 2006-02-24
Hi

I'm using ubuntu breezy connected to a broadband connection through a wireless router. There is another windows machine connected to the same router - on this I get downloads at 350-400kbps. But on the ubuntu machine i'm getting only 5-10kbps. I tried disabling ipv6 but still the speed is the same.

configuration: P3 750Mhz, 128 MB RAM, 20 GB HDD.

Thank you
Balaji

---

### Post by balaji on 2006-02-24
any ideas on this?:(

---

### Post by jamesr on 2006-02-24
Are you comparing the speeds on the same files from the same sites? and what software are you using to calculate the download speed.

---

### Post by balaji on 2006-02-24
i can't do anything apart from just browsing. I did compare speeds with the same file on the same site. It takes around 5 minutes to download a 100 KB pdf :( (don't even think about audio/video)

---

### Post by jamesr on 2006-02-25
Have you tryied exchanging the NICs or just changing the NIC in the Ubuntu system?
 Or changing the port on the router. ?
What are the NICs?
Are they both being seen in the same by the router?

There are test sites for checking speeds but I cannot remember any currently.

I sometimes use the appropriate local Ubuntu respository, to check speed.

Also when you ping the router what are your times like?

---

### Post by balaji on 2006-02-27
[QUOTE=jamesr]Have you tryied exchanging the NICs or just changing the NIC in the Ubuntu system?
 Or changing the port on the router. ?
What are the NICs?
Are they both being seen in the same by the router?

There are test sites for checking speeds but I cannot remember any currently.

I sometimes use the appropriate local Ubuntu respository, to check speed.

Also when you ping the router what are your times like?[/QUOTE]

i tried changing ports on the router - but to no effect.  The linux system is an old one - P3 750 Mhz while the windows one is a Celeron 2 Ghz system. will both NICs be exchangeable?


> What are the NICs?
Are they both being seen in the same by the router?

Could you explain this? I don't understand.

These are my ping results:

PING [www.yahoo.akadns.net](www.yahoo.akadns.net) (68.142.197.75) 56(84) bytes of data.
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=1 ttl=52 time=44.6 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=2 ttl=52 time=46.7 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=3 ttl=52 time=44.7 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=4 ttl=52 time=47.8 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=5 ttl=52 time=47.9 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=6 ttl=52 time=47.1 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=7 ttl=52 time=71.7 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=8 ttl=52 time=44.7 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=9 ttl=52 time=47.1 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=10 ttl=52 time=46.4 ms
64 bytes from p12.[www.mud.yahoo.com](www.mud.yahoo.com) (68.142.197.75): icmp_seq=11 ttl=52 time=54.5 ms

--- [www.yahoo.akadns.net](www.yahoo.akadns.net) ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10008ms
rtt min/avg/max/mdev = 44.623/49.408/71.751/7.526 ms


Thank you
Balaji

---

### Post by jamesr on 2006-02-27
What is that you want us to explain. but after rereading.

> Quote:
What are the NICs?
Are they both being seen in the same by the router?  


what are the NICs Network Interface Cards, the  brand,the type, ISA,PCI, PCMIA,WIRED and WIRELESS etc.
Are they both being seen at the same speed by the router.

The ping times that I was asking for was to the router eg for my router
ping 192.168.123.254

replace the 192.168.123.254 with what ever is appropriate for your router.

 Certainly the ping times are 3 times longer than my current times to google, but they  depend on the number of hops and individuals delays.

sudo tracepath [www.yahooakadns.net](www.yahooakadns.net)

---

### Post by balaji on 2006-02-27
[QUOTE=jamesr]What is that you want us to explain. but after rereading.


what are the NICs Network Interface Cards, the  brand,the type, ISA,PCI, PCMIA,WIRED and WIRELESS etc.
Are they both being seen at the same speed by the router.

The ping times that I was asking for was to the router eg for my router
ping 192.168.123.254

replace the 192.168.123.254 with what ever is appropriate for your router.

 Certainly the ping times are 3 times longer than my current times to google, but they  depend on the number of hops and individuals delays.

sudo tracepath [www.yahooakadns.net](www.yahooakadns.net)[/QUOTE]


results for pinging my router:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.31 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.28 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.38 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=1.28 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1.27 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=2.02 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=1.27 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=1.29 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=1.28 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=1.29 ms

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9007ms
rtt min/avg/max/mdev = 1.277/1.372/2.020/0.218 msIts a wired NIC

min/avg/max are all 1ms on the windows machine. Its a wired connection - connected with a LAN cable.

Thank you
Balaji

---

### Post by jamesr on 2006-02-27
the ping times were OK please supply the other requested info

---

### Post by balaji on 2006-02-28
On the windows machine

realtek rtl8139 family pci fast ethernet nic 

How can I see the NIC details on the linux machine? I searched for the command but couldn't find it.

Thank you
Balaji

---

### Post by jamesr on 2006-02-28
We, currently, do not need the the NIC information because we know that is working as shown by the ping to the router but for your infomation there are several ways

```
lspci
sudo mii_tool eth0

```

also```
dmesg |grep eth
```

Is the router dual speed 10/100Mbps?

```
sudo tracepath www.yahoo.akadns.net
```

As a direct comparision use the command

ping [www.yahoo.akadns.net](www.yahoo.akadns.net)

on both of the systems.

---

### Post by balaji on 2006-03-02
[QUOTE=jamesr]We, currently, do not need the the NIC information because we know that is working as shown by the ping to the router but for your infomation there are several ways

```
lspci
sudo mii_tool eth0

```

also```
dmesg |grep eth
```

Is the router dual speed 10/100Mbps?
[/QUOTE]

The tracepath command did not run fully.
 ```
balaji@silence:~$ sudo tracepath www.yahoo.akadns.net
 1:  192.168.1.102 (192.168.1.102)                          0.418ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.190ms
 2:  10.38.176.1 (10.38.176.1)                             26.691ms
 3:  gig-2-1.mplsmn09-rtr1.mn.rr.com (24.26.162.198)      asymm  4  23.854ms
 4:  srp0-1.mplsmn01-rtr2.mn.rr.com (24.26.162.2)          13.200ms
 5:  so0-1-2.chcgilL3-rtr1.kc.rr.com (24.94.160.13)       asymm  6  20.968ms
 6:  so0-0-2.kscymoL3-rtr1.kc.rr.com (24.94.161.105)       26.938ms
 7:  so-1-2-0-0.gar1.Denver1.Level3.net (4.71.40.1)       asymm 10  54.002ms
 8:  ge-2-3-0.bbr1.Denver1.Level3.net (4.68.124.213)      asymm  9  43.512ms
 9:  as-0-0.bbr1.Dallas1.Level3.net (209.247.11.22)        55.923ms
10:  ae-21-54.car1.Dallas1.Level3.net (4.68.122.109)      asymm  9  67.036ms
11:  4.79.180.10 (4.79.180.10)                            asymm 13  51.516ms
12:  no reply
13:  no reply
14:  no reply
15:  no reply

```

Ping result for Linux
```

balaji@silence:~$ ping www.yahoo.akadns.net
PING www.yahoo.akadns.net (68.142.197.66) 56(84) bytes of data.
64 bytes from p3.www.mud.yahoo.com (68.142.197.66): icmp_seq=1 ttl=51 time=44.8 ms
64 bytes from p3.www.mud.yahoo.com (68.142.197.66): icmp_seq=3 ttl=51 time=45.0 ms
64 bytes from p3.www.mud.yahoo.com (68.142.197.66): icmp_seq=4 ttl=51 time=45.1 ms
64 bytes from p3.www.mud.yahoo.com (68.142.197.66): icmp_seq=5 ttl=51 time=44.2 ms
64 bytes from p3.www.mud.yahoo.com (68.142.197.66): icmp_seq=6 ttl=51 time=43.8 ms

--- www.yahoo.akadns.net ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5003ms
rtt min/avg/max/mdev = 43.803/44.603/45.143/0.524 ms

```

Ping result for windows:


```

Pinging www.yahoo.akadns.net [68.142.197.73] with 32 bytes of data:

Reply from 68.142.197.73: bytes=32 time=43ms TTL=51
Reply from 68.142.197.73: bytes=32 time=45ms TTL=51
Reply from 68.142.197.73: bytes=32 time=44ms TTL=51
Reply from 68.142.197.73: bytes=32 time=44ms TTL=51

Ping statistics for 68.142.197.73:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

Approximate round trip times in milli-seconds:
    Minimum = 43ms, Maximum = 45ms, Average = 44ms

```

tracert on the windows system.
[CODE]
Pinging www.yahoo.akadns.net [68.142.197.73] with 32 bytes of data:Reply from 68.142.197.73: bytes=32 time=43ms TTL=51

Reply from 68.142.197.73: bytes=32 time=45ms TTL=51Reply from 68.142.197.73: bytes=32 time=44ms TTL=51Reply from 68.142.

197.73: bytes=32 time=44ms TTL=51Ping statistics for 68.142.197.73:    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss

),Approximate round trip times in milli-seconds:    Minimum = 43ms, Maximum = 45ms, Average = 44ms

Thank you
Balaji

---

### Post by jamesr on 2006-03-02
Looking at the ping times they seem to be very similar so I am wondering if the problem is not the networking  side on your PC

Sorry I should have asked for this information earlier.

 Although you should not be losing the connection path. It will be worth checking when you get a slow time, the ping times and the tracepath, see if the link is dropping a lot.

---

### Post by oyvindh on 2006-03-02
Upps

---

### Post by balaji on 2006-03-03
I tried the tests on [www.pcpitstop.com](www.pcpitstop.com)

Ping and trace tests gave similar results. 


Bandwidth test on the windows machine

Download speed: 4403 kilobits per second
Test details: 3354 kilobytes downloaded in 6.094 seconds.

Bandwidth test totally failed on the Linux machine.

The test did not complete at all.

---

### Post by leogoiano on 2006-05-11
A lot of people have that problem. I've read on a few posts here people saying they share an internet connection w/ windows and ubuntu machines(server runs ubuntu also) and the linux machines are having connection problems... I am one of them...
Ive read somewhere here someone saying that upgrading to dapper(server machine) could solve the problem... I tried it here but it didnt work for me.. I am going to try to install dapper on my clients machines also since now I use breezy... lets see what happens...

---

