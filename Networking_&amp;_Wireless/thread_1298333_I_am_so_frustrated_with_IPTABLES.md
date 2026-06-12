---
title: "I am so frustrated with IPTABLES"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by kixome on 2009-10-22
I think this applies to all distro's: 

I have been fighting with IPTABLES for a year or more now. I cannot even get a gui front-end to fix my problem. Here is the problem: Whenever I have iptables enabled, i cannot browse my local network shares from linux. Windows can browse the shares on my Lin box, but not the other way around. I have set rules in iptables/(and tried firestarter etc) to allow all traffic from inside the network to no avail, every rule I create for everything but SMB protocol works. browsing windows shares from linux in nautilus is the only thing that doesn't work properly.

I have tried different things i have read on the forums before posting, again to no avail.

if anyone has any ideas, please post up. Thanks everybody and anybody.

---

### Post by kixome on 2009-10-22
#here is my iptables setup:
#The NAT portion of the ruleset. Used for Network Address Transalation.
#Usually not needed on a typical web server, but it's there if you need it.
#*nat
#:PREROUTING ACCEPT [127173:7033011]
#:POSTROUTING ACCEPT [31583:2332178]
#:OUTPUT ACCEPT [32021:2375633]
#COMMIT

#The Mangle portion of the ruleset. Here is where unwanted packet types get dropped.
#This helps in making port scans against your server a bit more time consuming and difficult, but not impossible.
*mangle
:PREROUTING ACCEPT [444:43563]
:INPUT ACCEPT [233:43563]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [402:144198]
:POSTROUTING ACCEPT [402:144198]
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
COMMIT

#The FILTER section of the ruleset is where we initially drop all packets and then selectively open certain ports.
#We will also enable logging of all dropped requests.
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:LOG_DROP - [0:0]
:LOG_ACCEPT - [0:0]
:icmp_packets - [0:0]

#First, we cover the INPUT rules, or the rules for incoming requests.
#Note how at the end we log any incoming packets that are not accepted.
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 445 -j ACCEPT
-A INPUT -p udp -m udp --dport 445 -j ACCEPT
-A INPUT -p udp -m udp --dport 138 -j ACCEPT
-A INPUT -p udp -m udp --dport 137 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 137 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 139 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 135 -j ACCEPT
-A INPUT -p udp -m udp --dport 135 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -p udp -m udp --dport 43 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 43 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 51476 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 40262 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 46134 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 46133 -j ACCEPT
#uncomment the next line if you are running Spamassassin on your server
#-A INPUT -p tcp -m tcp --dport 783 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A INPUT -s 127.0.0.1 -j ACCEPT
-A INPUT -p icmp -j icmp_packets
-A INPUT -j LOG_DROP

#Next, we cover the OUTPUT rules, or the rules for all outgoing traffic.
#Note how at the end we log any outbound packets that are not accepted.
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 23 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 42 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 43 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 43 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 8080 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 143 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 445 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 445 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 445 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 138 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 137 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 137 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 139 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 135 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 135 -j ACCEPT
#uncomment the next line if you are running Spamassassin on your server
-A OUTPUT -p tcp -m tcp --dport 995 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 5050 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 5050 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 51476 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 40262 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 46133 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 46134 -j ACCEPT
-A OUTPUT -d 127.0.0.1 -j ACCEPT
-A OUTPUT -p icmp -j icmp_packets
-A OUTPUT -j LOG_DROP

#Here we have 2 sets of logging rules. One for dropped packets to log all dropped requests and one for accepted packets, should we wish to log any accepted requesets.
-A LOG_DROP -j LOG --log-prefix "[IPTABLES DROP] : " --log-tcp-options --log-ip-options
-A LOG_DROP -j DROP

-A LOG_ACCEPT -j LOG --log-prefix "[IPTABLES ACCEPT] : " --log-tcp-options --log-ip-options
-A LOG_ACCEPT -j ACCEPT

#And finally, a rule to deal with ICMP requests. We drop all ping requests except from our own server.
# Make sure you replace  with the IP address of your server.
-A icmp_packets -p icmp -m icmp --icmp-type 0 -j ACCEPT
-A icmp_packets -s 127.0.0.1 -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 11 -j ACCEPT
COMMIT

---

### Post by kixome on 2009-10-25
nobody knows iptables?

---

### Post by Lars Noodén on 2009-10-25
Nobody wants to debug the output from iptables. ;)  Without being able to test the connections, it's quite difficult. For example, how many network interfaces does your machine have?

What I would recommend is have it log blocked packets and then check the logs.  You can move the LOG target around from rule to rule as you debug.
One way is to have 100% open rules and log all new connections going out or coming while you go through and connect to all your services.  The go through the logs and try to make rules that match.  

At the same time you can also test from your machine using tcpdump or snort for passive monitoring or nmap for more active probing.

---

### Post by kixome on 2009-10-29
oh, well thanks, though this isn't iptables output, its a autoload script for iptables.

---

### Post by sliketymo on 2009-10-29
> **kixome said:**
> I think this applies to all distro's: 

I have been fighting with IPTABLES for a year or more now. I cannot even get a gui front-end to fix my problem. Here is the problem: Whenever I have iptables enabled, i cannot browse my local network shares from linux. Windows can browse the shares on my Lin box, but not the other way around. I have set rules in iptables/(and tried firestarter etc) to allow all traffic from inside the network to no avail, every rule I create for everything but SMB protocol works. browsing windows shares from linux in nautilus is the only thing that doesn't work properly.

I have tried different things i have read on the forums before posting, again to no avail.

if anyone has any ideas, please post up. Thanks everybody and anybody.

Just a wild guess,but you may have to set up sharing in your windows box,to allow the connection from your Linux.

---

### Post by mpokrywka on 2009-10-30
You iptables rules seem OK, what you get when you try from terminal:

smbclient -d 3 -L WINDOWS_MACHINE_NAME

(this will try to list shares on windows-machine with debug info)

---

