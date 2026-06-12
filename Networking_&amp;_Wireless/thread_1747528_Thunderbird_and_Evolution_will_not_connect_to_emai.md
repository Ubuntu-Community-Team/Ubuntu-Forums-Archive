---
title: "Thunderbird and Evolution will not connect to email server"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by mango.muncher on 2011-05-02
[FONT="Verdana"]
Hello, 
I am running Lucid 10.04, after upgrade I could not get Evolution to connect to my ISP's POP3 email server. 
So I loaded Thunderbird 3 and had another connection fault (Connection to server timed out). I spent time on phone with my ISP's tech support checking settings etc, all set OK.
So I created a Gmail account, followed Gmail set up for Thunderbird 3  [http://mail.google.com/support/bin/answer.py?answer=180189]("http://mail.google.com/support/bin/answer.py?answer=180189")and I have the same connection issue. "Connection to server xxxx timed out"

So now concentrating on setting up Thunderbird for GMail.Here is some info:
*Internet works fine, access through a router DLink DSL-502T
*During setup Thunderbird autofind of server settings fails, even after address and ports manually loaded in.
*Manual setup of IMAP server settings: imap.googlemail.com ; Port:993 ; SSL/TLS ; Normal Password
Outgoing Server settings: smtp.googlemail.com ; Port:465
*I can ping imap.googlemail.com
*I cannot telnet imap.googlemail.com 993 or smtp.googlemail.com 465
```
andrew@andrew-desktop:~$ telnet smtp.googlemail.com 465
Trying 1.0.0.0...
telnet: Unable to connect to remote host: Connection timed out
```
*ufw firewall is disabled

*ifconfig dump: Note I tried with ipv6 disabled, was still not connecting.
```
andrew@andrew-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:d8:66:51  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:e6ff:fed8:6651/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40060180 (40.0 MB)  TX bytes:3198244 (3.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7856 (7.8 KB)  TX bytes:7856 (7.8 KB)
```

So I am thinking that since upgrade the required ports are not open? But I not to sure where to go next.
Any suggestions appreciated.
Thanks.

[/FONT]

---

### Post by collisionystm on 2011-05-02
[FONT=Verdana]> andrew@andrew-desktop:~$ telnet smtp.googlemail.com 465WRONG!

Its not googlemail.com lol
[/FONT]



[SIZE=-1]
[/SIZE][SIZE=-1]**Incoming Mail (IMAP) Server - requires SSL:**[/SIZE] [FONT=Courier New, Courier, mono][SIZE=-1]imap.gmail.com[/SIZE][/FONT][SIZE=-1]
[/SIZE][SIZE=-1]**Use SSL**: Yes
[/SIZE]**Port 993**

**Ou**[SIZE=-1]**tgoing Mail (SMTP) Server - requires SSL:**[/SIZE] [FONT=Courier New, Courier, mono][SIZE=-1]smtp.gmail.com[/SIZE][/FONT][SIZE=-1] (use authentication)
**Use Authentication**: Yes
**Port for SSL**: 465 [/SIZE]   [SIZE=-1]**Account Name: **[/SIZE] [SIZE=-1]your full email address (including [FONT=Courier New, Courier, mono]@gmail.com[/FONT] or [FONT=Courier New, Courier, mono]@your_domain.com[/FONT]) [/SIZE]   [SIZE=-1]**Email Address: **[/SIZE] [SIZE=-1]your email address ([FONT=Courier New, Courier, mono]username@gmail.com[/FONT] or [FONT=Courier New, Courier, mono]username@your_domain.com[/FONT]) [/SIZE]   [SIZE=-1]**Password: **[/SIZE] [SIZE=-1]your Gmail password [/SIZE]

---

### Post by mango.muncher on 2011-05-02
[FONT="Verdana"]
Hi collisionystm,

This link Thunderbird 3 help page from Gmail [http://mail.google.com/support/bin/answer.py?answer=180189]("http://mail.google.com/support/bin/answer.py?answer=180189") uses imap.googlemail.com 

I tried with imap.gmail.com and smtp.gmail.com but still no connection


[/FONT]

---

### Post by collisionystm on 2011-05-02
> **mango.muncher said:**
> [FONT=Verdana]
Hi collisionystm,

This link Thunderbird 3 help page from Gmail [http://mail.google.com/support/bin/answer.py?answer=180189](http://mail.google.com/support/bin/answer.py?answer=180189) uses imap.googlemail.com 

I tried with imap.gmail.com and smtp.gmail.com but still no connection


[/FONT]


Change to imap.google.com and smtp.google.com

---

### Post by mango.muncher on 2011-05-02
imap.google.com and smtp.google.com failed to connect.

---

### Post by collisionystm on 2011-05-02
> **mango.muncher said:**
> imap.google.com and smtp.google.com failed to connect.


Well I just checked.

It is def.

imap.gmail.com
smtp.gmail.com


can you ping these?

I can....


> ping imcharles@MAWS5240:~$ ping imap.gmail.com
PING gmail-imap.l.google.com (74.125.115.109) 56(84) bytes of data.
64 bytes from vx-in-f109.1e100.net (74.125.115.109): icmp_req=1 ttl=51 time=57.6 ms
64 bytes from vx-in-f109.1e100.net (74.125.115.109): icmp_req=2 ttl=51 time=58.2 ms
^C
--- gmail-imap.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 57.672/57.978/58.284/0.306 ms
charles@MAWS5240:~$ 

---

### Post by mango.muncher on 2011-05-02
Yes I can ping imap.gmail.com and smpt.gmail.com

---

### Post by mango.muncher on 2011-05-03
[FONT="Verdana"]
I have solved this now.
I figured I needed to open some ports on my router.
As I was using a DSL-502T I used this support site [http://www.dlink.com.au/tech/Download/download.aspx?product=DSL-502T&revision=REV_A&filetype=Manuals]("http://www.dlink.com.au/tech/Download/download.aspx?product=DSL-502T&revision=REV_A&filetype=Manuals") and downloaded the info "How to open ports in DSL-502T"
Followed this and voila.

To clarify: I set a static IP on  my PC via the network applet (Or go to System/Administration/Network Tools change network device to "Ethernet Interface(etho) and punch "configure"). Select Auto Eth0 punch "edit" Select "IPV4" Change method to "manual" I added IP as 10.1.1.99 and Netmask as 255.0.0.0 and gateway 10.1.1.1
Then added in the DNS server address for my internet provider. This was important as I later found out when I was setting up 11.04 on a raid array and could not get Firefox or Thunderdird to connect again.


[/FONT]

---

### Post by tretiy3 on 2011-08-30
i can confirm that.
my laptop was connected via xp desktop, with ip adress "auto".

it was not possible to connect to google.com at all. not even mail server. sites which use google.com/jsapi were crashed.  i was not able to load them.

the solution is to set a static ip instead of 'auto'. just 192.168.0.whatever do not touch gateway or dns settings. just asign ip manualy.
it works

---

