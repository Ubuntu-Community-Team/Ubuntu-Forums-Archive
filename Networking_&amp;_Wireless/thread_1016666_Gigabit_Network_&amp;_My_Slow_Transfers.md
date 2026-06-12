---
title: "Gigabit Network &amp; My Slow Transfers"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by goatroapr on 2008-12-20
Hello.  I recently upgraded a few computers on my network with gigabit adapters (Intel Pro 1000), new CAT 6 cable and a new linksys WRT310N gigabit router. Although I see a speed improvement over my 10/100 router (was 7-8 MB/sec) I had but still am only getting 15MB/sec transfer from my Linux machine to Windows XP MCE machine. I have tried a few things including setting up Samba Server; I checked a few different posts but cannot come up with a solution. 

Here is my ipconfig:

```
jason@jason-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:21:2a:8e:e3  
          inet addr:160.200.100.101  Bcast:160.200.100.127  Mask:255.255.255.224
          inet6 addr: fe80::21b:21ff:fe2a:8ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98720658 (98.7 MB)  TX bytes:6380738 (6.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:19:66:28:45:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1956 (1.9 KB)  TX bytes:1956 (1.9 KB)
```

Here is my ethtool:

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
```

My hdparm:
```
/dev/sda:
 Timing buffered disk reads:  164 MB in  3.01 seconds =  54.52 MB/sec
```

Any suggestions would be appreciated.
Thanks,

---

### Post by iponeverything on 2008-12-20
You might be hitting a cpu bottleneck. 

What are the cpus on the test systems.

My squid server easily pushes past 50MB/sec 

Broadcom NetXtreme BCM5704 Gigabit Ethernet / tg3 driver

---

### Post by goatroapr on 2008-12-20
My fellow service member I presume? I'm in the Army working here at the US Embassy in Prague.
Interesting. Hope it isn't a problem though.  My Linux machine 2.66 Core 2 Duo w/2gb RAM DDR II and the MCE machine has an AMD 64 3600+ 2.21ghz with 2 gb RAM DDR

---

### Post by iponeverything on 2008-12-20
Wish I was in Prague, today is first day in three months that we could tell that we are surrounded by mountains. Though, I don't blame anyone for trying to keep warm. Power situation is quite bad for Kabul. 

I don't think your problem is cpu related, I would start looking drivers next. Is the XP box set to auto negotiation, what does it connect at?
Try booting the Ubuntu live CD on the XP machine and test transfer from Linux to Linux.

Do you get different throughput results going X-over from box to box?

---

### Post by iponeverything on 2008-12-20
strange,the last one was dup'ed.

---

### Post by goatroapr on 2008-12-20
It was cold here but got mid 40s last week. Hope it gets colder though, bad for skiing otherwise.

Yeah, shortly after my last post, I tried a transfer from my wifes computer, also a dual core, and actually, speeds were back in the 7-8 Mb/sec range but she has a 10/100 NIC anyway. Tried the live cd and still only around 15.  Barring I move the computer next to this one (in living room 50 ft cat 6 away), I can't test that and don't have a x-over cable.  The auto negotiate comes in at 1.0gb/s.

I failed to mention that I have my gigabit router connected to my DSL router but all settings, to include cable connections, are on the gigabit router and I can't see anything besides the internet going through the DSL router. Who knows though, perhaps that may be an issue?  Maybe theres a port I have to open between the two?

thanx

---

### Post by goatroapr on 2008-12-28
Still having the same issue. Will see if I can borrow a xover cable from work tomorrow.

---

### Post by alex004 on 2008-12-29
Hi goatroapr,

Seems I have the same problems. Since I use 8.10 on my Latitude D620, my network is incredibly slow. I asked several times in several forums without any useful results.
I only know for sure, that Windows as well as Ubuntu 7.04 does not have these problems.

br
alex

---

### Post by netztier on 2008-12-29
> **goatroapr said:**
> Yeah, shortly after my last post, I tried a transfer from my wifes computer, also a dual core, and actually, speeds were back in the 7-8 Mb/sec range but she has a 10/100 NIC anyway.

Run **iPerf** (it's a text mode tool you run from the shell) that you can install from the universe repositories. It measures raw TCP throughput. Samba still has protocol limitations - I never managed go get any faster transfer rates than roughly 20MBytes/s.


On the "server" (the machine *receiving* the data stream)
```
marc@blaze:~$ iperf -s
```
on the "client" (the machine *sending* the data stream)
```
marc@cube:~$ iperf -c <server's IP> -i 5 -t 30
```

This will give you a 30sec sample with result output every 5sec. Be sure to swap "server" and "client" roles to spot any irregularities and see what you get. This should easily be in the 600-700Mbps range, depending on how your Gigabit NICs are connected to the system (directly on the bus/chipset, PCI-Express. PCI-X or plain PCI). 

My venerable P-III 500MHz with a PCI-based Intel Pro/1000 GT NIC gives numbers in the high 500Mbit/s range (no jumbo frames, no playing around with window sizes and the like).

Not all onboard-NICs are connected to the system bus, however. The Shuttle barebone I have here has it behind a PCI bridge - slows it down considerably :-(


regards

Marc

---

### Post by goatroapr on 2009-01-04
Hi Marc,

I installed a gig NIC in the wifes computer and here are my results.
Mine to hers:

  3] local 160.200.100.102 port 57214 connected with 160.200.100.106 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec    552 MBytes    927 Mbits/sec
[  3]  5.0-10.0 sec    550 MBytes    923 Mbits/sec
[  3] 10.0-15.0 sec    550 MBytes    922 Mbits/sec
[  3] 15.0-20.0 sec    549 MBytes    922 Mbits/sec
[  3] 20.0-25.0 sec    552 MBytes    926 Mbits/sec
[  3] 25.0-30.0 sec    550 MBytes    923 Mbits/sec
[  3]  0.0-30.0 sec  3.23 GBytes    924 Mbits/sec
jason@jason-desktop:~$ 


Hers to mine:

[  3] local 160.200.100.106 port 52488 connected with 160.200.100.102 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec    549 MBytes    921 Mbits/sec
[  3]  5.0-10.0 sec    548 MBytes    920 Mbits/sec
[  3] 10.0-15.0 sec    548 MBytes    920 Mbits/sec
[  3] 15.0-20.0 sec    547 MBytes    918 Mbits/sec
[  3] 20.0-25.0 sec    548 MBytes    919 Mbits/sec
[  3] 25.0-30.0 sec    548 MBytes    919 Mbits/sec
[  3]  0.0-30.0 sec  3.21 GBytes    919 Mbits/sec
elsa@Elsa:~$ 

Seems like it is working as promised. Perhaps its the other things you mentioned.  If that is the case, please let me know so I stop worrying about it. :-)  Also, my NICs are on the PCI bridge. Never thought of that one but makes complete sense too.

Thanks,
Jason

---

### Post by bsh on 2009-01-04
i have reached 60+mb/s on pci cards. but since the server has a pci-e intel pro 1000pt, and the clients are all pci-e cards, i can reach the limit of the hard drive, using ftp. (sambe is always behind, but i could push it up to 40mb/s)
your iperf results tell me that your network is configured well, seems like auto tcp windows scaling and stuff is working well.
try to install vsftpd (or another ftp server) and try transferring using that, it usually gives a good measure of you network speed.
there are also many optimizations for samba, to crank the speed up, but it will always be slower.

---

### Post by netztier on 2009-01-06
> **goatroapr said:**
> 
Seems like it is working as promised. Perhaps its the other things you mentioned.  If that is the case, please let me know so I stop worrying about it. :-)


These numbers are among the best I've ever seen reported by iPerf, and I've seen it running on other beasts than what you can buy as a "PC".

Most definitely, your network is in very good shape, no duplex issues, no bad cables, and the whole TCP self-tuning as well, just like bsh said.

You may now dive into the dark pool of Samba optimization - you might find a clue or two there - but beware of tuning guides referring to old samba versions - and that includes the one in samba's own documentation - the hints I found in there did not help at all (at least in my case).

You might want to consider NFS as well. It performs very well, but has it's own set of configuration issues, of course.  And you can't use it from "Places -> Connect to Server", which reduces it's comfort of use a bit: NFS-mounts must be done from /etc/fstab or by the root user.


regards

Marc

---

### Post by goatroapr on 2009-01-07
Thanks netztier and bsh. I will try NFS and/or optimizing samba and see what comes of it.

Cheers,
Jason

---

