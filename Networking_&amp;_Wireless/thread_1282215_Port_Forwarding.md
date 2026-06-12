---
title: "Port Forwarding"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by jen140 on 2009-10-04
Hello all.
I need help forwarding any connection from internet (eth0) on port 21 to a lan machine (eth1), more exaclty to 192.168.0.200:21.
I've tryied many rules with iptables i've found in google but none worked.
My network starting script:
#!/bin/sh
PATH=/usr/sbin:/sbin:/bin:/user/bin
#dhclient eth0
ifconfig eth1 192.168.0.1
ifconfig eth1 up
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X
iptables -P FORWARD ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
######
And i've also tryied addiing the next rule:
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 21 -j DNAT --to-destination 192.168.0.200:21
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
And tryied to connect through lan (eth1) , localhost (lo) and tryied scanning with nmap remotely.
And nmap shows 21 is filtered, but not open.

---

### Post by ermeyers on 2009-10-04
First off.  At a glance, I don't see a "sysctl -w net.ipv4.ip_forward=1" to tell the kernel it's okay.

---

### Post by jen140 on 2009-10-04
Sorry forgot to say about that part:
server:/proc/sys/net/ipv4# cat ip_forward
1
All the network works and from lan computers i can access the internet.

---

### Post by ermeyers on 2009-10-04
Okay.  I assume that you don't have router hardware, because now your trying to be a router.  I know how to do it in router hardware, but I'll take a look into this, because I'm interested in knowing this too.

---

### Post by jen140 on 2009-10-04
Yes, thise machine needs to be the router, because I dont have any other router hardware.

---

### Post by ermeyers on 2009-10-04
file:///usr/share/doc/iptables/html/NAT-HOWTO-3.html

**Destination NAT** (DNAT)
Destination NAT is when you alter the destination address of the first packet: i.e. you are changing where the connection is going to. Destination NAT is always done before routing, when the packet first comes off the wire.  Port forwarding, load sharing, and transparent proxying are all forms of DNAT.

file:///usr/share/doc/iptables/html/NAT-HOWTO-6.html#ss6.2

## Change destination addresses of web traffic to 5.6.7.8, port 8080.
# iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 5.6.7.8:8080
> 
I need help forwarding any connection from internet (eth0) on port 21 to a lan machine (eth1), more exaclty to 192.168.0.200:21.
Given:
eth0 -> WAN
eth1-> LAN = 192.168.0.0

```

## Change destination addresses of FTP(=21) traffic to 192.168.0.200, port 21.
# iptables -t nat -A PREROUTING -p tcp --dport 21 -i eth0 -j DNAT --to 192.168.0.200:21

```Try that.

---

### Post by jen140 on 2009-10-04
Ok,i've tryied but when i try to connect from lan, it doesnt report any error and just drops the connection.
With nmap i scanned localhost and 192.168.0.1, and the port wasnt shown.
Also tryied the service nmap-online.com and it shows that 21 is filtered.
Tryied nmap from lan, and it doesnt show the 21 either.
And when i connect directly to 192.168.0.200 on port 21 i get connected.

---

### Post by ermeyers on 2009-10-04
> **jen140 said:**
> Ok,i've tryied but when i try to connect from lan, it doesnt report any error and just drops the connection.
With nmap i scanned localhost and 192.168.0.1, and the port wasnt shown.
Also tryied the service nmap-online.com and it shows that 21 is filtered.
Tryied nmap from lan, and it doesnt show the 21 either.
And when i connect directly to 192.168.0.200 on port 21 i get connected.
This DNAT statement is only working on the eth0/WAN interface, so any eth1/LAN attempt will still be dependent upon an FTP server running on the 192.168.0.1 machine.  Try running a sniffer on eth1 to see if anything is passing over.

---

### Post by jen140 on 2009-10-04
Thank i will ask to someone connect to it, if it is possible :
83.132.157.116
You should get the next header : "220 ---freeFTPd 1.0---warFTPd 1.65---"

---

### Post by ermeyers on 2009-10-04
Did you clean out your other iptables attempts?

$ telnet 83.132.157.116 21
Trying 83.132.157.116...
^C
$ telnet 83.132.157.116 22
Trying 83.132.157.116...
telnet: Unable to connect to remote host: Connection refused

---

### Post by jen140 on 2009-10-04
I've done the next:
server:/proc/sys/net/ipv4# iptables -F
server:/proc/sys/net/ipv4# iptables -t nat -F
server:/proc/sys/net/ipv4# iptables -P FORWARD ACCEPT
server:/proc/sys/net/ipv4# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
server:/proc/sys/net/ipv4# iptables -t nat -A PREROUTING -p tcp --dport 21 -i eth0 \
>         -j DNAT --to 192.168.0.200:21
And ssh is only accessible from lan.

---

### Post by ermeyers on 2009-10-04
$ nmap 83.132.157.116

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-10-04 05:28 EDT
Interesting ports on a83-132-157-116.cpe.netcabo.pt (83.132.157.116):
Not shown: 993 closed ports
PORT     STATE    SERVICE
21/tcp   filtered ftp
25/tcp   filtered smtp
53/tcp   open     domain
111/tcp  open     rpcbind
5222/tcp open     unknown
5269/tcp open     unknown
5280/tcp open     unknown

Nmap done: 1 IP address (1 host up) scanned in 11.26 seconds

---

### Post by jen140 on 2009-10-04
So what i need to do to forward the port ? :\
And btw, what is the "beam" service, that was listening on 5222,5269 and 5280?
And another thing, i have the next in hosts.allow:
rpcbind: 128.192.
rpcbind: 10.10.
rpcbind: 127.0.
#
and nothing in hosts.deny:

---

### Post by ermeyers on 2009-10-04
$ telnet 83.132.157.116 25
Trying 83.132.157.116...                     
^C
$ telnet 83.132.157.116 111
Trying 83.132.157.116...                      
Connected to 83.132.157.116.                  
Escape character is '^]'.

^]
telnet> quit

---

### Post by jen140 on 2009-10-04
Rcpbind shouldnt only listen on lan/localhost ?
PS: 
Maybe the problem is that the 192.168.0.200 is running on the same machine as the "router", under VirtualBox?

---

### Post by ermeyers on 2009-10-04
-F, --flush [chain]
              Flush the selected chain (all the chains in the table if none is
              given).   This  is  equivalent  to deleting all the rules one by
              one.
       -P, --policy chain target
              Set the policy for the chain to the given target.  See the  sec&#8208;
              tion  TARGETS  for  the legal targets.  Only built-in (non-user-
              defined) chains can have  policies,  and  neither  built-in  nor
              user-defined chains can be policy targets.

Edit /etc/rc.local
```

#NAT
sysctl -w net.ipv4.ip_forward=1
iptables -P FORWARD ACCEPT

#SNAT
iptables --table nat -A POSTROUTING --out-interface eth0 -j MASQUERADE

#DNAT
iptables --table nat -A PREROUTING --in-interface eth0 -j DNAT -p tcp --dport 21 --to 192.168.0.200:21

```thinking ...

---

### Post by jen140 on 2009-10-04
Ok, i've removed my script (/etc/network/if-up.d/00-firewall) that i showed before, and added the lines you asked me, what i need to do now ? Reboot ?

---

### Post by ermeyers on 2009-10-04
Yeah do a reboot.

file:///usr/share/doc/iptables/html/NAT-HOWTO-8.html

---

### Post by jen140 on 2009-10-04
The problem persists, and now i cant ping google from the local machine.
Port 21 is still filtered.

---

### Post by ermeyers on 2009-10-04
I googled "iptables dnat forwarding passive ftp" and other "passive" ports might need to be forwarded.

Look at this first:
[http://www.linuxquestions.org/questions/linux-security-4/iptables-and-passive-ftp-behind-the-nat-92579](http://www.linuxquestions.org/questions/linux-security-4/iptables-and-passive-ftp-behind-the-nat-92579)


[http://linuxpoison.blogspot.com/2008/11/ftp-port-forwarding-using-iptables.html](http://linuxpoison.blogspot.com/2008/11/ftp-port-forwarding-using-iptables.html)
   Might try:
   "-I PREROUTING" rather than "-A PREROUTING"
   "--to-destination 192.168.0.200" rather than "--to 192.168.0.200:21"

[http://www.experts-exchange.com/Security/Linux_Security/Q_20652062.html](http://www.experts-exchange.com/Security/Linux_Security/Q_20652062.html)
   Maybe iptables -A INPUT [COLOR=#F78200]__[/COLOR]-i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT # Allow _incoming _[COLOR=#F78200]__[/COLOR] traffic

---

### Post by ermeyers on 2009-10-04
Here's a command to use: iptables -nvL

I've got Church coming up, so i'll check you later. --Eric

---

### Post by jen140 on 2009-10-04
DOnt think it needs passive to send the ftp header.
2nd command, gives the same result ( filtered ).
Tryied the 3rd command, same result.


server:/home/jen140# iptables -nvL
Chain INPUT (policy ACCEPT 17187 packets, 1626K bytes)
 pkts bytes target     prot opt in     out     source               destination 
    2    80 ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT 93376 packets, 88M bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 19478 packets, 9026K bytes)
 pkts bytes target     prot opt in     out     source               destination 
server:/home/jen140#

---

### Post by ermeyers on 2009-10-04
I've gotto go until after 12 noon EST.  [http://www.linuxquestions.org/questions/linux-security-4/iptables-and-passive-ftp-behind-the-nat-92579](http://www.linuxquestions.org/questions/linux-security-4/iptables-and-passive-ftp-behind-the-nat-92579) has a lot of stuff:

# open ports to the firewall
echo "	applying the open port(s) to the firewall rules"
echo ""
$iptables -A INPUT -p tcp --dport 21 -j ACCEPT

# enable passive ftp transfers
echo "	opening passive FTP ports"
echo ""
$iptables -A INPUT -p tcp --sport 5151 --dport 5151 -m state --state ESTABLISHED -j ACCEPT
$iptables -A OUTPUT -p tcp --sport 5151 --dport 5151 -m state --state ESTABLISHED,RELATED -j ACCEPT

# enable active ftp transfers
echo "	opening active FTP ports"
echo ""
$iptables -A INPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A OUTPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT

Let me know, if you get it. --Eric

---

### Post by jen140 on 2009-10-04
I've run iptables -A INPUT -p tcp --dport 21 -j ACCEPT
And nmap-online.com still reports its filtered =(.
Tryied also the rest commands:
iptables -A INPUT -p tcp --sport 5151 --dport 5151 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 5151 --dport 5151 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
Same state, filtered, but the interesting part is that now its not showing other ports that were filtered 135,139,445.
Maybe the nmap-online scanner doesnt work as it should?
I always thougth that port forwarding under linux was much easier than in windows ( cause there we need external apps ), and the ideia of rebooting also reminds me of windows.

---

### Post by jen140 on 2009-10-04
So, any ideias ?

---

### Post by ermeyers on 2009-10-04
Unfortunately my DSL provider has me hidden inside a 192.168.1.0 network, so I can't emulate the outside too well.  Between the two machines in my LAN, I'll try to see what works.  So, I'll have to get back with you.  Keep trying.

---

### Post by jen140 on 2009-10-05
Mirror of the post on debian forum : [http://forums.debian.net/viewtopic.php?f=10&t=45715](http://forums.debian.net/viewtopic.php?f=10&t=45715)

---

### Post by ermeyers on 2009-10-05
Did some investigating with regard to iptables and package ufw.  Verify "ufw status" is "Status: inactive".  In /etc/sysctl.conf it has "net.ipv4.ip_forward=1" uncommented, and /etc/ufw/sysctl.conf it has "#net/ipv4/ip_forward=1" commented.

---

### Post by jen140 on 2009-10-06
bash: ufw: command not found
# cat /etc/sysctl.conf |grep ip_fo
net.ipv4.ip_forward=1
Ip forwarding works.

---

### Post by jen140 on 2009-10-06
The problem is still not solved, arent there any pro linux admins out here?

---

### Post by ermeyers on 2009-10-06
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by jen140 on 2009-10-07
Thanks ermeyers, you are only one who's still here trying to help, but,
In the given tutorial UFW doesnt describe port forwarding.
And given command in the tutorial didnt worked :
iptables -A FORWARD -s 0/0 -i eth0 -d 192.168.0.200 -o eth1 -p TCP \
         --sport 1024:65535 --dport 135 -j ACCEPT
My friend tryied to connect with putty and got connection refused, nmap-online.com reported the port as filtered.

---

### Post by ermeyers on 2009-10-07
I have the UFW from a Desktop install, so it was just an FYI for you, and the Linux Home Networking article at least gives you a good diagram to think with.[URL="http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables"]
[/URL]

---

### Post by jen140 on 2009-10-08
Yes, its really a good reading, but mostly when I have everything is working.
I'm really using debian, and installed the base system, after i've installed the app's that i neded.

---

### Post by jen140 on 2009-10-11
Thanks every one for your time and help.
I've got it solved at [http://www.daniweb.com/forums/thread229187.html](http://www.daniweb.com/forums/thread229187.html)
The problem was on the side of the virtual machine.

---

