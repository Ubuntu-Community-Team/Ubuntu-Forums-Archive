---
title: "Bind DNS server setup - I'm about to commit suicide !!!"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by qwbb on 2011-06-28
Dear all,

After many hours of hair pulling, I've got 2 options: to ask for help or commit suicide !! :(

I've installed bind9 on my brand new Ubuntu 10.04 server. I've read ~*50 sites explaining how to set it up, and it should be OK.
When I run dig on the server, it works OK, indeed.

BUT when I try to access from the outside World, dig says (replaced my server IP with xx.xx.xx.xx) :

; <<>> DiG 9.4.3-P3 <<>> +norec @xx.xx.xx.xx google.com
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached


I checked with nmap -p53 xx.xx.xx.xx

Starting Nmap 4.90RC1 ( [http://nmap.org](http://nmap.org) ) at 2011-06-28 23:49 CEST
Interesting ports on xxxxx.com (xx.xx.xx.xx):
PORT   STATE  SERVICE
53/tcp closed domain

Nmap done: 1 IP address (1 host up) scanned in 0.46 seconds


But why ????
On the server, I check netstat -plantu :

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      3081/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      6163/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4031/apache2    
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      876/java        
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      13446/named     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      22441/sshd      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      13446/named     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      5195/master     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      6163/dovecot    
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN      876/java        
tcp        0     64 xx.xx.xx.xx:22         yy.yy.yy.yy:64512      ESTABLISHED 6413/1          
tcp        0      0 xx.xx.xx.xx:22         yy.yy.yy.yy:64514      ESTABLISHED 6718/sshd: root@not
tcp6       0      0 ::1:53                  :::*                    LISTEN      13446/named     
tcp6       0      0 :::22                   :::*                    LISTEN      22441/sshd      
tcp6       0      0 ::1:953                 :::*                    LISTEN      13446/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           13446/named     
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2966/dhclient3  
udp6       0      0 ::1:53                  :::*                                13446/named     


And my firewall is open : iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FWKNOP_INPUT (0 references)
target     prot opt source               destination         


WHY ??? :(

---

### Post by Sylslay on 2011-06-28
ask for help is easy and less hassel.... no body...

be happy..

everybody got insurance number ... to pay tax LOL.

---

### Post by qwbb on 2011-06-28
Thanks to give me a sign that I'm not alone... BTW, do you have any idea that could help me to get my server to respond to DNS requests?
:)
Thanks!

---

### Post by qwbb on 2011-06-29
BTW, if you need to see any configuration file to answer my question, please ask! :)
Thanks for your help!

---

### Post by Sylslay on 2011-06-29
Last march I instaled full LAMP server on Ubuntu 10.04.

I setup everyting.
I browese www page on local network.

But When I put IP address from oustide network doesn't work.

I figure out that router ADSL is not set wright.

Even if I used OpenDNS and setup account , still can't seen my webpage at net...

Not much help from me, sorry is above my exp...

---

### Post by qwbb on 2011-06-29
A friend of mine finally found the solution !!!

Removing the following line from named.conf.options did the trick !!!

listen-on port 53 { 127.0.0.1; };


Apparently, the DNS was only listening to its own requests, but not to those from the outside World.
I wonder why this line got in there...

---

### Post by Sylslay on 2011-07-01
127.0.0.1 is loop back addres, :-)

---

### Post by collisionystm on 2011-07-01
> **qwbb said:**
> A friend of mine finally found the solution !!!

Removing the following line from named.conf.options did the trick !!!

listen-on port 53 { 127.0.0.1; };


Apparently, the DNS was only listening to its own requests, but not to those from the outside World.
I wonder why this line got in there...


That is because you can use Bind9 to have forwarders.

It will answer local requests and requests from itself, and if no entries match its records, it will forward to your ISP Dns

---

### Post by Iowan on 2011-07-01
WHEW! Glad to hear that suicide was averted - at least for now...

---

### Post by qwbb on 2011-07-04
> **Iowan said:**
> WHEW! Glad to hear that suicide was averted - at least for now...

;)

Thanks to all for your help. Indeed it's not easy to setup a server.
Since most of us want to setup a simple Web server, I wonder whether there is a "typical" setup, or "typical" /etc/ directory for comparison: it would help to diff files and check obvious things.

Do you know whether this exists somewhere?

Thanks again!

---

