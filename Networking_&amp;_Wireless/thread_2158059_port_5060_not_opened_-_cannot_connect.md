---
title: "port 5060 not opened - cannot connect"
date: 2013-06-27
forum: Networking &amp; Wireless
---

### Post by spindler on 2013-06-27
I am installing Asterisk 11 and I am having some issues with the port.  I  have opened the port on the IPtable and my router also ha sport 5060  open.  Everything looks like it is configured correctly. However when I  attempt a SIP call to the server I cannot connect.   I also used a  telnet command from a computer on my LAN and I could not see 5060.

Here is the information I have

UBUNTU 11.10  information

root@ubuntu-s2:/$ sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1538/exim4      
tcp        0      0 192.168.1.185:3306      0.0.0.0:*               LISTEN      931/mysqld      
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      10609/asterisk  
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1623/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      807/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      779/cupsd       
tcp6       0      0 ::1:25                  :::*                    LISTEN      1538/exim4      
tcp6       0      0 :::22                   :::*                    LISTEN      807/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      779/cupsd       
udp        0      0 0.0.0.0:40655           0.0.0.0:*                           766/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           766/avahi-daemon: r
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:4520            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10609/asterisk  
udp6       0      0 :::5353                 :::*                                766/avahi-daemon: r
udp6       0      0 :::41416                :::*                                766/avahi-daemon: r

AS YOU CAN SEE 5060 IS LISTED AND ASSOCIATED WITH ASTERISK. 
The IPTABLE SHOWS THE FOLLOWING:

ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:10000:20000 


WHEN  I LOOK AT MY ROUTER I CAN SEE THE PORT IS OPEN.    I have port 5060 open as a UDP port. 


WHEN I USE TELNET PORT 5060 IS NOT AVAILABLE.  THE COMMAND I AM USING IS THE FOLLOWING:

telnet  192.168.1.23 5060  and  I cannot establish a connection.

I also went to the following website to test the connection.   [http://www.overpie.com/web-tools/port-scanning-tool](http://www.overpie.com/web-tools/port-scanning-tool)

So why can I not establish a connection with my server?

---

### Post by compiledkernel on 2013-06-27
> **spindler said:**
> I am installing Asterisk 11 and I am having some issues with the port.  I  have opened the port on the IPtable and my router also ha sport 5060  open.  Everything looks like it is configured correctly. However when I  attempt a SIP call to the server I cannot connect.   I also used a  telnet command from a computer on my LAN and I could not see 5060.

Here is the information I have

UBUNTU 11.10  information

root@ubuntu-s2:/$ sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1538/exim4      
tcp        0      0 192.168.1.185:3306      0.0.0.0:*               LISTEN      931/mysqld      
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      10609/asterisk  
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1623/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      807/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      779/cupsd       
tcp6       0      0 ::1:25                  :::*                    LISTEN      1538/exim4      
tcp6       0      0 :::22                   :::*                    LISTEN      807/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      779/cupsd       
udp        0      0 0.0.0.0:40655           0.0.0.0:*                           766/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           766/avahi-daemon: r
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:5000            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:4520            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           10609/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10698/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10655/asterisk  
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           10609/asterisk  
udp6       0      0 :::5353                 :::*                                766/avahi-daemon: r
udp6       0      0 :::41416                :::*                                766/avahi-daemon: r

AS YOU CAN SEE 5060 IS LISTED AND ASSOCIATED WITH ASTERISK. 
The IPTABLE SHOWS THE FOLLOWING:

ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:10000:20000 


WHEN  I LOOK AT MY ROUTER I CAN SEE THE PORT IS OPEN.    I have port 5060 open as a UDP port. 


WHEN I USE TELNET PORT 5060 IS NOT AVAILABLE.  THE COMMAND I AM USING IS THE FOLLOWING:

telnet  192.168.1.23 5060  and  I cannot establish a connection.

I also went to the following website to test the connection.   [http://www.overpie.com/web-tools/port-scanning-tool](http://www.overpie.com/web-tools/port-scanning-tool)

So why can I not establish a connection with my server?

Here is my iptables config from my asty box. 


 iptables -A INPUT -p udp -m udp --dport 5060 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 4569 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 5036 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 10000:20000 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 2727 -j ACCEPT

Your missing a couple of those.

---

### Post by spindler on 2013-06-27
> **compiledkernel said:**
> Here is my iptables config from my asty box. 


 iptables -A INPUT -p udp -m udp --dport 5060 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 4569 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 5036 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 10000:20000 -j ACCEPT
 iptables -A INPUT -p udp -m udp --dport 2727 -j ACCEPT

Your missing a couple of those.

Thanks. I was able to add those additional iptable values.   However, I am still not able to communicate to the port.  It is very weird.   Here is my "COMPLETE"  IP TABLE.

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:10000:20000 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:4569 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:2727 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5036 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137 
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138 
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68 
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 4 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251         udp dpt:5353 
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250     udp dpt:1900 
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:80 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20 
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:20 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:21 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:22 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:25 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:8080 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:443 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:5060 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5060 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination

---

### Post by compiledkernel on 2013-06-27
I need more than a few minutes to disseminate that.

Question: So when you attempt a call you dont get anything in asterisk's logs, and your not generating CDRs in /var/log/asterisk/cdr-csv?

---

### Post by spindler on 2013-06-27
I do not think I am connecting to the server.   There are no log messages and when I use a port testing tool I do not see port 5060 is open.

---

### Post by compiledkernel on 2013-06-27
Whats between you and the asterisk instance?

---

### Post by spindler on 2013-06-27
I am running Zoiper (a VOIP softphone) on a mac computer.  This computer is connected to a wireless gateway via wifi.  The server is connect to this gateway via ethernet. The server is running Ubuntu 11.10.
On the server I am running Asterix.

When I call the asterisk server using Zoiper the phone cannot be register.
When I test the ports using telnet from the MAC I can see that port 80 and 22 are open.  Port 5060 is closed.

The gateway has many ports open including 80,22,5060(udp) and 10000-20000.

The gateway also has access to the internet.  When I use the port testing tool [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)    I can see that port 80,22 are open.  Ports 5060 and 10000-20000 are closed.

---

### Post by spindler on 2013-06-27
I am also running ufw.  

80                         ALLOW       Anywhere
20                         DENY        Anywhere
21                         DENY        Anywhere
22                         ALLOW       Anywhere
25                         DENY        Anywhere
8080                       ALLOW       Anywhere
443                        ALLOW       Anywhere
5060/udp                   ALLOW       Anywhere
5060                       ALLOW       Anywhere
8080                       ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)
5060/udp                   ALLOW       Anywhere (v6)
5060                       ALLOW       Anywhere (v6)

---

### Post by spindler on 2013-06-28
I replaced my router(gateway) with a network switch(Dynex model DX-ESW5) to eliminate any concerns with my router. I connected my MAC computer to the switch with a Ethernet cable and the Server to the same switch with an Ethernet cable.   Using telnet on a terminal I was able to duplicate the error using the switch so I am 100% sure there is something wrong with the Ubuntu Server.  

Port 5060 on my Ubuntu machine is not open. Very weird......  :confused:


Any help you can give would be appreciated.:)

---

### Post by spindler on 2013-06-28
Learning new things is always good.  After pocking around the internet I found some information about UDP ports.....  Telnet does not test UDP ports very well. Here is the link I read.

[http://adityo.blog.binusian.org/?p=787](http://adityo.blog.binusian.org/?p=787)

Using this information.  I downloaded  nmap onto my MAC computer.

[http://nmap.org/download.html#macosx](http://nmap.org/download.html#macosx)

Then I used nmap to probe port 5060 of my server.   I got back the following:


USING MY EXTERNAL IP ADDRESS

Chriss-MacBook-Air:~ chris$ sudo nmap -p 5060 -sU -P0 XXX.XXX.XXX.XXX

Starting Nmap 6.25 ( [http://nmap.org](http://nmap.org) ) at 2013-06-28 16:18 MDT
Nmap scan report for S0106.xxxxxx.net (XXX.XXX.XXX.XXX)
Host is up.
PORT     STATE         SERVICE
5060/udp open|filtered sip

THIS SHOWS THAT PORT 5060  IS OPEN!

NOW WHEN I CHECK USING AN INTERAL IP ADDRESS.


Chriss-MacBook-Air:~ chris$ sudo nmap -p 5060 -sU -P0 192.168.1.185

Starting Nmap 6.25 ( [http://nmap.org](http://nmap.org) ) at 2013-06-28 16:18 MDT
Nmap scan report for 192.168.1.185
Host is up (0.0022s latency).
PORT     STATE  SERVICE
5060/udp closed sip
MAC Address: 00:15:C5:5E:EE:D8 (Dell)


THIS SHOWS PORT 5060 IS CLOSED.

This is very weird.   I need to go for a walk.

---

