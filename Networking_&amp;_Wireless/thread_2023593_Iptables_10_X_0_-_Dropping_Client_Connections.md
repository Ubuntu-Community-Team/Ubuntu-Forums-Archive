---
title: "Iptables 10 X 0 - Dropping Client Connections"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by Wisdown on 2012-07-12
Good Night People,

The first thing i need say is: English isnt my native language, so i hope you guys can understand me.

I`m here fightining on last 3 days against Iptables, and i`m getting owned :(
If someone would provide an link where i can find hints how to fix my problem, or, give any hint i would be grateful.
I need say i`m total newbie with basic knowledge on IPtables / BIND9, i`m learning all stuff now ;)

My system is using Ubuntu Server 12.04

Its installed DHCP / BIND9
The server have 3 NICs supposed to work this way:

eth0 = Internet (Waiting my ISP give the valid IP)
eth1 = Servers (will host some websites also)
eth2 = Workstations

As soon i get the valid i will host some websites.
I`m not sure if i did the correct setup on BIND9.
The two networks Servers and Workstations will need have some sharing like:
HTTP / FTP / MySQL


I did an script to load the firewall on boot with this settings:

#####################################
# Cleaning previous setup #
#####################################

iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X
iptables -t nat -X
iptables -t mangle -X
iptables -Z
iptables -t nat -Z
iptables -t mangle -Z


#############################
# Security Setup   #
#############################

# tcp_syncookies = Protection against SYN Flood Atack
echo "1" > /proc/sys/net/ipv4/tcp_syncookies

# icmp_echo_ignore_all = Dont accept External Ping
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all

# icmp_echo_ignore_broadcasts = Dont Accept ICMP 
# Broadcasts and Multicasts
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# icmp_ignore_bogus_error_responses = Ignore Fake Messages and Erros about ICMP
echo "1" >  /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

for i in /proc/sys/net/ipv4/conf/*; do
    # Dont redirect ICMP Messages
    echo 0 > $i/accept_redirects

    # Protection against IP Spoofing Atacks
    echo 0 > $i/accept_source_route

    # Kernel Choose if answer by same address or not
    echo 1 > $i/arp_filter

    # Log Fake Packets
    echo 1 > $i/log_martians

    # Check for valid Address of packets
    # (Protection Against IP Spoofing)
    echo 1 > $i/rp_filter
done

###################
# Default Politic #
###################

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Bind9
iptables -A INPUT -p udp --dport 53 -j ACCEPT

# DHCP
iptables -A INPUT -i eth1 -p udp --sport 68 --dport 67 -j ACCEPT
iptables -A INPUT -i eth2 -p udp --sport 68 --dport 67 -j ACCEPT

# DNS
iptables -A FORWARD -o eth0 -p udp -m multiport --dports 53,5353 -j ACCEPT

# FTP
iptables -A FORWARD -o eth0 -p tcp --dport 21 -j ACCEPT

# HTTP
iptables -A FORWARD -o eth0 -p tcp -m multiport --dports 80,8080 -j ACCEPT

# HTTPS - Protocolo de Transferencia de Hypertext Seguro
iptables -A FORWARD -o eth0 -p tcp --dport 443 -j ACCEPT

###########################
# COMPARTILHANDO INTERNET #
###########################

# Masquerade
iptables -t nat -A POSTROUTING -s 10.0.0.0/255.255.255.0 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 192.168.1.0/255.255.255.0 -o eth0 -j MASQUERADE

# ip_forward = Redirect IP pakcets
echo "1" > /proc/sys/net/ipv4/ip_forward


####################################
# Problems with this setup: #
####################################

1 - My DHCP clients get random Drop, sometimes they are dropped  every 5 min, other times every 30 min, there no standard to check this behavior...

2 - MSN is working, i was think since the default politic i set as DROP for all without an rule the MSN shouldnt work.

3 - DHCP dont give more IP after sometime for dropped clients, then i need restart Server + Client

4 - On /var/log/syslog there lots of martians log, i know i can disable those messagens but i guess this should b helpfull

5 - At server trying use "apt-get update" / "apt-get upgrade" i get an error message (I need open an specific port?)

6 - When i try restart the server the shutdown took around 5 min on message: "Stopping domain name service... bind9"

7 - When i try restart the Server the shutdown took around 3 min on message: "Deconfiguring network interfaces"

------------------------------------------------------------------------------------------
Dont setting IPtables and letting everything oppened, the problems from the list above  are:
4 - 6 - 7
For let everything open i use this:
------------------------------------------------------------------------------------------


#####################################
# Cleaning Previous Stuff #
#####################################

iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X
iptables -t nat -X
iptables -t mangle -X
iptables -Z
iptables -t nat -Z
iptables -t mangle -Z

###################
# Default Politic #
###################

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT


###########################
# SHARING INTERNET #
###########################

iptables -t nat -A POSTROUTING -s 10.0.0.0/255.255.255.0 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 192.168.1.0/255.255.255.0 -o eth0 -j MASQUERADE


echo "1" > /proc/sys/net/ipv4/ip_forward

------------------------------------------------------------------------------------------

Withthis last script i dont get my workstations with the random drop issu, the internet works pretty well in all networkings.
With the first script i get random DROPs on eth1 and eth2.

The drops would be because i`m missing any forward rule?

Thanks in advice.

---

### Post by miegiel on 2012-07-12
**[COLOR="DarkOrange"]Wisdown[/COLOR]** can you post the output of
```
sudo iptables-save
```
or
```
sudo iptables-save -c
```
for me. The rules make more sense to me that way (iptables bash scripts make my head spin :D). And post it in a code box please (the **#** button in the post editor).

That said, you should edit the corresponding config files to apply stuff like
```
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
```
as configured setting during boot. You shouldn't run it every time you start the firewall.

And if you do 
```
iptables -F
```
it's not necesary to also do
```
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
```

And if you have a fixed IP address for your internet connection, it's recommended not to use *-j MASQUERADE*, but to use *-j SNAT*. For example:
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source *xxx.xxx.xxx.xxx*
```
Where *xxx.xxx.xxx.xxx* is your internet IP.

---

### Post by Wisdown on 2012-07-12
Hey Miegel,

Thanks for your reply!!!

Here my Settings with Firewall ON:

################################################

# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:28 2012
*nat
:PREROUTING ACCEPT [4:1063]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [3:984]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
COMMIT
# Completed on Thu Jul 12 23:16:28 2012
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:28 2012
*mangle
:PREROUTING ACCEPT [37:10453]
:INPUT ACCEPT [5:2136]
:FORWARD ACCEPT [32:8317]
:OUTPUT ACCEPT [3:984]
:POSTROUTING ACCEPT [32:8317]
COMMIT
# Completed on Thu Jul 12 23:16:28 2012
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:28 2012
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [3:984]
-A INPUT -i eth0 -p tcp -m tcp --dport 135 -j DROP
-A INPUT -p tcp -m multiport ! --dports 0:1056 -j DROP
-A INPUT -p udp -j DROP
-A INPUT -p icmp -j DROP
-A INPUT -m limit --limit 3/min --limit-burst 3 -j LOG --log-prefix "LOG-FW: "
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth2 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A FORWARD -o eth0 -p udp -m multiport --dports 53,5353 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m tcp --dport 21 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m multiport --dports 80,8080 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
COMMIT
# Completed on Thu Jul 12 23:16:28 2012


###########################################


Now my settings with firewall off:


############################################


# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:47 2012
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
COMMIT
# Completed on Thu Jul 12 23:16:47 2012
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:47 2012
*mangle
:PREROUTING ACCEPT [7:1727]
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [7:1727]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [7:1727]
COMMIT
# Completed on Thu Jul 12 23:16:47 2012
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:47 2012
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [7:1727]
:OUTPUT ACCEPT [0:0]
COMMIT
# Completed on Thu Jul 12 23:16:47 2012


PS.: Thanks for the hints about redundancy in my script, i`m updating this now.

---

### Post by miegiel on 2012-07-12
I added 1 rule for you
```
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:28 2012
*nat
PREROUTING ACCEPT [4:1063]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [3:984]
POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
-A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
COMMIT
# Completed on Thu Jul 12 23:16:28 2012
# Generated by iptables-save v1.4.12 on Thu Jul 12 23:16:28 2012
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [3:984]
-A INPUT -i eth0 -p tcp -m tcp --dport 135 -j DROP
-A INPUT -p tcp -m multiport ! --dports 0:1056 -j DROP
-A INPUT -p udp -j DROP
-A INPUT -p icmp -j DROP
-A INPUT -m limit --limit 3/min --limit-burst 3 -j LOG --log-prefix "LOG-FW: "
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth2 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A FORWARD -o eth0 -p udp -m multiport --dports 53,5353 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m tcp --dport 21 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m multiport --dports 80,8080 -j ACCEPT
-A FORWARD -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
**[COLOR="Red"]-A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT[/COLOR]**
COMMIT
# Completed on Thu Jul 12 23:16:28 2012
```
If you save it to a file you can load it on the server with:
```
cat file.name | sudo iptables-restore
```
The rule allows all output except for invalid packets, so you traffic out is not firewalled. I also removed the mangle table, since it wasn't doing anything.

---

### Post by miegiel on 2012-07-12
Now don't be intimidated, this is just for inspiration ;)

Here's the firewall of the gateway that connects my LAN to the web. It's not doing anything but running a time-service and ssh and of course connecting me to the internet (the *italic stuff* is anonymized).

```
# Generated by iptables-save v1.4.8 on Thu Jul 12 21:06:24 2012
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:BLACKLISTED - [0:0]
-A INPUT -i eth1 -m recent --rcheck --name EVIL --rsource -j DROP 
-A INPUT -i eth1 -m recent --update --seconds 1234 --name STUPID --rsource -j BLACKLISTED 
-A INPUT -m state --state INVALID -j DROP 
-A INPUT -m state --state ESTABLISHED -j ACCEPT 
-A INPUT -d *www.www.www.www*/32 ! -i eth1 -j REJECT --reject-with icmp-host-unreachable 
-A INPUT -d 10.0.0.1/32 ! -i eth0 -j DROP 
-A INPUT -d 127.0.0.0/8 ! -i lo -j DROP 
-A INPUT -i eth1 -p udp -m multiport --dports 49152:65535,8500,500 -j REJECT --reject-with icmp-port-unreachable 
-A INPUT -i eth1 -p tcp -m multiport --dports 49152:65535,8500,500 -j REJECT --reject-with tcp-reset 
-A INPUT -s 10.0.0.0/8 ! -i eth1 -p udp -m multiport --dports 5351,137,67 -j DROP 
-A INPUT -i eth1 -p icmp -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[ ICMP   IN   ] " --log-level 7 
-A INPUT -p icmp -m icmp ! --icmp-type 5 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[ SSH    IN N ] " --log-level 7 
-A INPUT -p tcp -m tcp --dport 22 --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -m limit --limit 20/hour --limit-burst 2 -m recent --set --name SSH --rsource -j ACCEPT 
-A INPUT -s 10.0.0.0/8 ! -i eth1 -p udp -m udp --dport 123 -m state --state NEW -j ACCEPT 
-A INPUT -p udp -m udp --dport 33434:33534 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 33434:33534 -j ACCEPT 
-A INPUT -s 127.0.0.1/32 -d 127.0.0.1/32 -i lo -p udp -m udp --dport 123 -m state --state NEW -j ACCEPT 
-A INPUT -p tcp -m tcp ! --dport 22 ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j REJECT --reject-with tcp-reset 
-A INPUT -m recent --update --seconds 54321 --name SUSPECT --rsource -m recent --set --name STUPID --rsource -j BLACKLISTED 
-A INPUT ! -s *isp.isp.0.0*/16 -i eth1 -p tcp -m tcp --dport 1024:49151 -m recent --set --name SUSPECT --rsource -j REJECT --reject-with tcp-reset 
-A INPUT ! -s *isp.isp.0.0*/16 -i eth1 -p udp -m udp --dport 1024:49151 -m recent --set --name SUSPECT --rsource -j REJECT --reject-with icmp-port-unreachable 
-A INPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[        IN D ] " --log-level 7 
-A INPUT ! -s *isp.isp.0.0*/16 -i eth1 -m recent --set --name SUSPECT --rsource -j DROP 
-A FORWARD -i eth1 -m recent --rcheck --name EVIL --rsource -j DROP 
-A FORWARD -i eth1 -m recent --update --seconds 1234 --name STUPID --rsource -j BLACKLISTED 
-A FORWARD -o eth1 -m recent --rcheck --seconds 1234 --name STUPID --rdest -j BLACKLISTED 
-A FORWARD ! -p icmp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -i eth1 ! -o eth1 -p udp -m multiport --dports 6881:6882,*skypeport*,*secretport1* -m state --state NEW -j ACCEPT 
-A FORWARD -i eth1 ! -o eth1 -p tcp -m multiport --dports 6881:6882,*skypeport*,*secretport2*,*secretport3*,*secretport4* -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j ACCEPT 
-A FORWARD -d 172.16.0.0/12 -o eth1 -j REJECT --reject-with icmp-net-unreachable 
-A FORWARD -s 10.0.0.0/8 ! -i eth1 -o eth1 -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j ACCEPT 
-A FORWARD -s 10.0.0.0/8 ! -i eth1 -o eth1 ! -p tcp -m state --state NEW -j ACCEPT 
-A FORWARD -p icmp -m icmp ! --icmp-type 5 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD ! -i eth1 -o eth1 -p tcp -m multiport --dports 143,220,109,110,25,993,995,1109,106,465 -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m state --state INVALID -j ACCEPT 
-A FORWARD -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j REJECT --reject-with tcp-reset 
-A FORWARD -p tcp -m tcp --tcp-flags FIN,RST NONE -m state --state INVALID -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[        FW I ] " --log-level 7 
-A FORWARD ! -p tcp -m state --state INVALID -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[        FW I ] " --log-level 7 
-A FORWARD -m state --state INVALID -j DROP 
-A OUTPUT -o eth1 -p icmp -m icmp --icmp-type 3/1 -j DROP 
-A OUTPUT -o eth1 -m recent --rcheck --seconds 1234 --name STUPID --rdest -j BLACKLISTED 
-A OUTPUT -s 169.254.0.0/16 -o eth1 -j DROP 
-A OUTPUT -m state --state RELATED -m recent --rcheck --name SUSPECT --rdest -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[ SSPCT OUT R ] " --log-level 7 
-A OUTPUT -m state --state RELATED -j ACCEPT 
-A OUTPUT -o eth1 -p tcp -m tcp --sport 22 -m state --state ESTABLISHED -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[ SSH   OUT E ] " --log-level 7 
-A OUTPUT -m state --state ESTABLISHED -j ACCEPT 
-A OUTPUT -d *isp.isp.servers.0*/22 -o eth1 -p udp -m multiport --dports 123,67 -m state --state NEW -j ACCEPT 
-A OUTPUT -p udp -m multiport --dports 53,33434:33534 -m state --state NEW -j ACCEPT 
-A OUTPUT -p tcp -m multiport --dports 80,443,33434:33534 -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j ACCEPT 
-A OUTPUT -p tcp -m tcp --tcp-flags FIN,RST NONE -m state --state INVALID -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[       OUT I ] " --log-level 7 
-A OUTPUT ! -p tcp -m state --state INVALID -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[       OUT I ] " --log-level 7 
-A OUTPUT -m state --state INVALID -j DROP 
-A OUTPUT -p icmp -m state --state NEW -j ACCEPT 
-A OUTPUT -s 127.0.0.1/32 -d 127.0.0.1/32 -o lo -p udp -m udp --dport 123 -m state --state NEW -j ACCEPT 
-A OUTPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j REJECT --reject-with tcp-reset 
-A OUTPUT -m recent --rcheck --seconds 54321 --name SUSPECT --rdest -m recent --set --name STUPID --rdest -j BLACKLISTED 
-A OUTPUT ! -d *isp.isp.0.0*/16 -o eth1 -m recent --set --name SUSPECT --rdest -j DROP 
-A OUTPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "[       OUT D ] " --log-level 7 
-A BLACKLISTED -m recent --rcheck --hitcount 20 --name SUSPECT --rsource -m recent --set --name EVIL --rsource 
-A BLACKLISTED -d *www.www.www.www*/32 -i eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD   IN D ] " --log-level 7 
-A BLACKLISTED -i eth1 -o eth0 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD I FW D ] " --log-level 7 
-A BLACKLISTED -i eth1 -o wlan0 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD I FW D ] " --log-level 7 
-A BLACKLISTED -i eth1 -o pan0 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD I FW D ] " --log-level 7 
-A BLACKLISTED -i eth1 -o lo -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD I FW D ] " --log-level 7 
-A BLACKLISTED -i eth1 -j DROP 
-A BLACKLISTED -i eth0 -o eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD O FW D ] " --log-level 7 
-A BLACKLISTED -i wlan0 -o eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD O FW D ] " --log-level 7 
-A BLACKLISTED -i pan0 -o eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD O FW D ] " --log-level 7 
-A BLACKLISTED -i lo -o eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD O FW D ] " --log-level 7 
-A BLACKLISTED -s *www.www.www.www*/32 -o eth1 -m limit --limit 1000/day --limit-burst 20 -j LOG --log-prefix "[ STPD  OUT D ] " --log-level 7 
-A BLACKLISTED -j REJECT --reject-with icmp-host-unreachable 
COMMIT
# Completed on Thu Jul 12 21:06:24 2012
# Generated by iptables-save v1.4.8 on Thu Jul 12 21:06:24 2012
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -i eth1 -p udp -m multiport --dports 6881,*skypeport* -j DNAT --to-destination 10.0.0.3 
-A PREROUTING -i eth1 -p tcp -m multiport --dports 6881,*skypeport* -j DNAT --to-destination 10.0.0.3 
-A PREROUTING -i eth1 -p tcp -m multiport --dports 80,443,8080 -j DNAT --to-destination 10.0.0.3:*skypeport* 
-A PREROUTING -i eth1 -p tcp -m multiport --dports 25,109,110 -j DNAT --to-destination *www.www.www.www*:22 
-A PREROUTING -i eth1 -p tcp -m multiport --dports 6882,*secretport2*,*secretport3*,*secretport4* -j DNAT --to-destination 10.0.0.2 
-A PREROUTING -i eth1 -p udp -m multiport --dports 6882,*secretport1* -j DNAT --to-destination 10.0.0.2 
-A POSTROUTING -o eth1 -j SNAT --to-source *www.www.www.www* 
COMMIT
# Completed on Thu Jul 12 21:06:24 2012
```

---

### Post by Wisdown on 2012-07-12
Hey,

I`m testing now, bu i changed the:

```
-A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```For

```
-A OUTPUT -o eth2 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```I dindt get the valid IP yet, i`m waiting for my ISP approve the request.
With the Valid IP i wanna host some servers in a virtual private network eth1 (so i cant open all to web), then i will sell host services for some friends ;)

For avoid trouble i`m trying keep the eth2 as my private LAN on this one i gonna try set the admin access to servers runing eth1.

From eth1 (servers) to eth0 (WAN) i wanna let open only DNS (Bind9 - not sure if i did the correct setup / i think need wait the valid ip to test) / Apache 80-8008 / Mail 25 and 110 i think, and only this for avoid attacks

For get those access could you point me the right direction?
For example, From eth2 (192.168.0.0) what i need add to allow access my apache in eth1 (10.0.0.0) using only the ports 80 - 8080



Till now, i dindt get dropped, but my /var/log/syslog is getting alot of martion source coming from my notebook runing windows 7, this should be an virus or the servers i have installed? (Mysql / Apache  / MSSQL / etc...)

Thanks for your help, i`m getting a better understood how this work now ;)


Updating the Status
I tested now, and i cant connect on MSSQL in my desktop on same network my notebook is 192.168.1.5 my desktop is 192.168.1.6.
I`m getting connection timeouts issues on same newtork
But no more drop over internet.

---

### Post by miegiel on 2012-07-13
Martians are, as far as I know, packets sent by a LAN IP address to the internet interface (maybe also packets sent by an internet IP address to a LAN interface).

With the
```
-A OUTPUT -o eth2 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```
rule your server won't send any packets to the eth0 and eth1 interfaces. Just that you are aware. To (temporarily) avoid sending packets to the eth0 (internet) interface you could also use :
```
-A OUTPUT ! -o eth1 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```
*! -o eth1* means *not out eth1* or *any interface but eth1*.

I haven&#8217;t done anything with bind9 yet, I just use my isp's dns servers. But to allow incoming dns and http packets to your server you'll need rules like :
```
-A INPUT -m state --state ESTABLISHED -j ACCEPT 
-A INPUT -p tcp -m multiport --dports 80,8080 -m state --state NEW -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -m state --state NEW -j ACCEPT
```
The first rule is to allow established connections and the other 2 are for the first packet to establish a connection.

And to allow a response to go out you'll only need :
```
-A OUTPUT -m state --state ESTABLISHED -j ACCEPT
```
because the connection has already been established by the incoming connection.

By using a rule that allows all established connections you can make a rule that catches all those packets at the beginning of your chain of rules. So that those packets don't need to go through the whole chain and get dealt with fast. That the new packets travel further down the chain and are dealt with slower isn't a big deal, since there is only one of them for every new connection. And this way you can just focus on blocking new connections. A blocked new connection will never become established ;)

That's the beauty of statefull fire walls like iptables. They keep track of the connections (with conntrack) so you can handle the bulk of the traffic fast and focus the rules on just the new (and related,invallid) connections, saving CPU time.

I don't know if you like reading (partially out dated) tech, but I found these usefull:
[LIST]
[*][http://www.iptables.org/documentation/index.html](http://www.iptables.org/documentation/index.html)
[*][http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables)
[*][http://snowman.net/projects/ipt_recent/](http://snowman.net/projects/ipt_recent/)
[*][http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)
[/LIST]

*edit:*
I haven&#8217;t don anything with MSSQL either, but it's possible it's trying to talk to *lo* ( 127.0.0.0/8 ), my time-service does that too. Put a logging rule at the end of the in- and output chains. Then you can see what packets are not being accepted by your rules.
```
-A INPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "end chain in  " --log-level 7 
-A OUTPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "end chain out " --log-level 7 
```

To see the log:
```
sudo tail -n 100 /var/log/syslog
```
(on my debian server anyway, the ubuntu logs might have a different location)

---

### Post by Wisdown on 2012-07-13
Thank you for the Log:

```
-A INPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "end chain in  " --log-level 7
-A OUTPUT -m limit --limit 1000/day --limit-burst 50 -j LOG --log-prefix "end chain out " --log-level 7
```Now i can track some of the problems ^^

Looking the syslog, seems i need forward the dhcp, there some messages like this from my notebook:

```
... OUT=eth2 SRC=192.168.1.1 DST=192.168.1.5 LEN 328 TOS 0x00 PREC=0X00 TTL=64 ID=0 DF PROTO=UDP SPT=6 DPT=68 LEN=308
```The next message come as:

```
send_packet: Operation not permitted
```

And then lot of martians packets start, all from my notebook trying do broadcast:

```
ll header: ff:ff:ff:ff:ff:ff00:16:36:DE:84:AA:08:00
martian source 192.168.1.255 from 192.168.1.5 on dev eth0
```

I dont know how or why my notebook is trying broadcast on the eth0 (WAN), i was think the firewall was blocking all brodcast with this:

```
# icmp_echo_ignore_broadcasts = Dont Accept ICMP
# Broadcasts and Multicasts
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
```

And runing back my old script, i get the exact point where i get my connection dropped, the syslog says:

```
net_ratelimit: 8 callbacks suppressed
```

Then i get an fast drop and reconnected
I`m reading now the links you provide, thank you very much for the help ;)

---

### Post by Wisdown on 2012-08-07
Just updating this post.  After lot of problems and researchs, i see ubuntu have some "hidden" mechanics how to make the things work, for example, after my researches i discovered my shutdown taking so long was happening because an app called RNDC, my firewall rules wasnt able the port 953 get connected by this app, making this app hold the shutdown process for around 3 min... And lot of other issues where an Ubuntu expert probaly would deal easy, this make me think about how easy is Ubuntu for beginners?  I did an try with same setup using debian... And for my surprise got evertyhing working without problems...  The expert knowledge necessary to do the things imo so goes to Ubuntu who isnt easy to newbies like me...  Thanks for all support btw, but i will stay with Debian.

---

