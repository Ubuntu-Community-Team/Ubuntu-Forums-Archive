---
title: "Strange ADSL problem."
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Dean1982 on 2009-02-05
Hello all, I am a new and very happy user of UBUNTU ( why I have used windows for so long I do not know ).

I am wondering if it would be possible for someone to help this new user out ? 

I have installed Ubuntu 8.10 and have a recurring problem with my ADSL not being recognised at startup, I run Sudo pppoeconf and the system still does not recognise it.

However if I go into my partitioned windows XP the ADSL is recognised and works fine.

Here comes the unusual ( to me ) part.

If I go back into Ubuntu after using XP internet, it functions fine, saying "connected to the WIRED network", its almost like using it in XP allows UBUNTU to recognise it. ( odd ? ).

I can not think what is going wrong here, maybe I have configured it wrong.

I do notice on the grub selection screen, I have a number of Ubuntu's at different dates, which I do not presume is normal, could this be a factor ? 

Anyway I thank you for any help you can give me, I apologise I am new to this system, but I am very eager to learn and very excited by the possibilities.

Thank you so much all.

---

### Post by Dean1982 on 2009-02-15
I have tried checking the Kernel is installed properly and everything is fine. 

It is incredibly odd, I have now established that the connection works every time if I load up windows first.

I could not really find anything online that could be causing this. 

Any ideas ? It is almost as if Windows causes the ADSL to boot up again in Linux which makes no sense to me.

Gracious gracious thanks for any help you guys can give me, if I can get the internet working everytime I will never need use windows again.

---

### Post by Dean1982 on 2009-02-17
Ok, so I have checked sudo gedit /etc/network/interfaces

and received the following information

"auto lo
iface lo inet loopback"

Ifconfig when the internet works in ubuntu displays the following.

eth0      Link encap:Ethernet  HWaddr 00:26:54:0f:13:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:aa:ce:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x9000 

eth2      Link encap:Ethernet  HWaddr 00:05:1b:00:41:e1  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1bff:fe00:41e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118138959 (118.1 MB)  TX bytes:4911003 (4.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)

The thing that puzzles me is the connection working everytime without fail if I log on using windows first, then use Ubuntu afterwords, in some way I feel I would be able to resolve the issue easier if the wired network did not connect at all in ubuntu, it is the sporadic nature of the problem that is troubling.

Again thanks if anyone can help me.

---

### Post by puppywhacker on 2009-02-17
Hi,

your problem is very weird, there is not much information to go on. your eth2 has ip-address 192.168.0.3 which is an internal address. otherwise I have no clue about your connections. like you mentioned pppoeconf, but that is only needed if you have to login to your adsl-account, which is not very popular in europe. you have three other interfaces that might confuse the network manager. You have shown your interfaces file to be virtually empty which means that the network manager is supposed to take care of establishing connections, but it works best on very simple network setups. Also it's a bit puzzling why your adsl would work if it has been connected via XP. There is virtually nothing which windows can influence on the NIC. some odd fireware and registers maybe but those should not matter. maybe it's the operator who opens the connection in some way that you don't execute in linux in the same way. In that case pppoe might be the reason, if you restart in linux the connection is already established....

you see. I'm just as puzzled as you are. I'm puzzled because I don't know enough about your network. could you execute these commands? although it's more a shot in the dark than a long shot ... goodluck anyway

```
route
iptables -L -v
dig www.google.com
ping 192.168.0.1
ping www.google.com
```

---

### Post by Dean1982 on 2009-02-17
> **puppywhacker said:**
> Hi,

your problem is very weird, there is not much information to go on. your eth2 has ip-address 192.168.0.3 which is an internal address. otherwise I have no clue about your connections. like you mentioned pppoeconf, but that is only needed if you have to login to your adsl-account, which is not very popular in europe. you have three other interfaces that might confuse the network manager. You have shown your interfaces file to be virtually empty which means that the network manager is supposed to take care of establishing connections, but it works best on very simple network setups. Also it's a bit puzzling why your adsl would work if it has been connected via XP. There is virtually nothing which windows can influence on the NIC. some odd fireware and registers maybe but those should not matter. maybe it's the operator who opens the connection in some way that you don't execute in linux in the same way. In that case pppoe might be the reason, if you restart in linux the connection is already established....

you see. I'm just as puzzled as you are. I'm puzzled because I don't know enough about your network. could you execute these commands? although it's more a shot in the dark than a long shot ... goodluck anyway

```
route
iptables -L -v
dig www.google.com
ping 192.168.0.1
ping www.google.com
```


Thanks so much for your help, I really is completely appreciated.

Here is my report back. 

dean@dean-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         [www.routerlogin](www.routerlogin) 0.0.0.0         UG    0      0        0 eth2
dean@dean-desktop:~$ iptables -L -v
iptables v1.4.0: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
dean@dean-desktop:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.5.0-P2 <<>> [www.google.com](www.google.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30398
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.google.com](www.google.com).			IN	A

;; ANSWER SECTION:
[www.google.com](www.google.com).		601709	IN	CNAME	[www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com).	111	IN	A	216.239.59.104
[www.l.google.com](www.l.google.com).	111	IN	A	216.239.59.103
[www.l.google.com](www.l.google.com).	111	IN	A	216.239.59.99
[www.l.google.com](www.l.google.com).	111	IN	A	216.239.59.147

;; Query time: 31 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb 17 23:27:33 2009
;; MSG SIZE  rcvd: 116

dean@dean-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=1.57 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=1.03 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=0.913 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=255 time=0.767 ms


This is after logging on to windows, my network is connecting to an isp ( pipex ) via adsl.

I use a usb router/modem "Netgear DG834G", which is part of a tiny wireless network ( one other system being a laptop ).

Once again it worked perfectly after connecting in Windows XP, in fact it works every time after booting up windows XP first.

As a test I deleted the non essential network components ( the ones that do not connect ) to see if a simplified set up would help anything and I still got the same problem.

Thanks so much for your help, even if I can not resolve this it has been a great learning experience ( learning that not everything can be fixed ).

---

### Post by Dean1982 on 2009-02-17
Here is my results from when the network on Ubuntu does not work ( in case anyone can recognise a discrepancy or difference that I am to new to this to recognise ).

route 
iptables -L -v 
dig [www.google.com](www.google.com) 
ping 192.168.0.1 
ping [www.google.co](www.google.co) 



; <<>> DiG 9.5.0-P2 <<>> [www.google.com](www.google.com) 
;; global options:  printcmd 
;; connection timed out; no servers could be reached 
dean@dean-desktop:~$ ping 192.168.0.1 
connect: Network is unreachable 
dean@dean-desktop:~$ ping [www.google.co](www.google.co) 
ping: unknown host [www.google.co](www.google.co) 
dean@dean-desktop:~$ 
dean@dean-desktop:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
dean@dean-desktop:~$ iptables -L -v 
iptables v1.4.0: can't initialize iptables table `filter': Permission denied (you must be root) 
Perhaps iptables or your kernel needs to be upgraded. 
dean@dean-desktop:~$ dig [www.google.com](www.google.com) 

; <<>> DiG 9.5.0-P2 <<>> [www.google.com](www.google.com) 
;; global options:  printcmd 
;; connection timed out; no servers could be reached 
dean@dean-desktop:~$ ping 192.168.0.1 
connect: Network is unreachable 
dean@dean-desktop:~$ ping [www.google.co](www.google.co) 
ping: unknown host [www.google.co](www.google.co) 


Thanks again.

---

### Post by puppywhacker on 2009-02-18
From your output it shows that 192.168.0.1 is your adsl modem also acting as DNS server. The rest is not relevant

OK, I googled on PIPEX a bit and I found they are using PPPoA (point to point protocol over ATM) which is a bit different than PPPoE (over Ethernet)

Basically they use PPP to authenticate you as a user, you do this in windows, log in the linux and your link survives. It is simulated dail-up connection over ADSL using the ATM layer rather than the Ethernet layer.

I'm not sure but in linux you can use pppd (probably in combination with pppoeconf or wvdial) to connect to your internet privder.

Googling a bit more I found somebody posted his pppd settings for his pipex connection and that may help you further.

```
interface ATM0
no ip address
no atm ilmi-keepalive
atm vc-per-vp 64
dsl operating-mode auto
pvc 0/38
encapsulation aal5mux ppp dialer
dialer pool-member 1

interface Dialer 1
encapsulation ppp
dialer pool 1
dialer-group 1
ppp authentication chap pap callin
ppp chap hostname (isp_username)
ppp chap password (isp_password)
ppp pap sent-username (isp_username) password
```

I would experiment a few days with pppd to get the big picture and start a new thread about what you run into.

goodluck

---

### Post by Dean1982 on 2009-02-18
> **puppywhacker said:**
> From your output it shows that 192.168.0.1 is your adsl modem also acting as DNS server. The rest is not relevant

OK, I googled on PIPEX a bit and I found they are using PPPoA (point to point protocol over ATM) which is a bit different than PPPoE (over Ethernet)

Basically they use PPP to authenticate you as a user, you do this in windows, log in the linux and your link survives. It is simulated dail-up connection over ADSL using the ATM layer rather than the Ethernet layer.

I'm not sure but in linux you can use pppd (probably in combination with pppoeconf or wvdial) to connect to your internet privder.

Googling a bit more I found somebody posted his pppd settings for his pipex connection and that may help you further.

```
interface ATM0
no ip address
no atm ilmi-keepalive
atm vc-per-vp 64
dsl operating-mode auto
pvc 0/38
encapsulation aal5mux ppp dialer
dialer pool-member 1

interface Dialer 1
encapsulation ppp
dialer pool 1
dialer-group 1
ppp authentication chap pap callin
ppp chap hostname (isp_username)
ppp chap password (isp_password)
ppp pap sent-username (isp_username) password
```

I would experiment a few days with pppd to get the big picture and start a new thread about what you run into.

goodluck

Wow thanks for your input, I would love to be able to solve this, I feel I am getting closer thanks to your help, I am doing my research on pppd and will post a new thread if I can resolve this issue.

My modem is not recognised in either pppoeconf or wvdial, which makes things even more interesting.

I even tried an app called ubudsl, but that would not recognise my modem either.

Seems like for the time being I may be stuck needing Windows as a back up.

---

