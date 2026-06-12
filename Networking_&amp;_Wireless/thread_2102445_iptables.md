---
title: "iptables"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2013-01-07
```
#!/bin/bash

######################
#
#  Settings up variables for the script
#
######################
echo "setting up variables"
_ethOUT=eth1
    #_ethOUT is DHCP from ISP (outgoing interface)
_ethIN=eth0
dhclient $_ethOUT
#echo $_ethOUT
#_ethIN is static 10.1.1.5 and 10.1.1.1 it is also the bridge for VMs
_GATEWAY=$(ifconfig $_ethOUT | grep -v inet6 | grep inet | cut -d : -f 2 | sed 's/Bcast//')
echo $_GATEWAY
echo "The gateway inteface is $_ethOUT and its IP is $_GATEWAY"
echo "The internal interface is $_ethIN"

_FTP=10.1.1.5
_RUNUO=10.1.1.7
_CYGNENOS=10.1.1.3
_myDNS=$_CYGNENOS
_myDHCP=$_CYGNNOS
_Win2k8Server=10.1.1.9
_OpenDNS=208.67.222.222
_Player=10.1.1.19

########################
#
#   Flushing and setting defaults accepts
#
######################
echo "Flushing and setting defaults"
echo "  flush nat"
iptables -t nat -F
#iptables -P INPUT ACCEPT
echo "  flush input"
iptables -F INPUT
echo "  flush nat prerouting"
iptables -t nat -F PREROUTING
echo "  flush nat postrouting"
iptables -t nat -F POSTROUTING
echo "  flush output"
iptables -F OUTPUT
iptables -P OUTPUT ACCEPT
echo "  flush forward"
iptables -F FORWARD
iptables -P FORWARD ACCEPT

##########################
#
# ICMP
#
##########################
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT


################
#
# Masqurading
#
#################
echo "setting up masqurading"
# only need the one outgoing interface for internet access
iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE


################
#
# INPUT
#   - IN TO THIS SERVER
#
###############
echo "setting up INPUT"
# default states
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# ntp from local server
iptables -A INPUT -p udp -i $_ethIN --dport 123 -j ACCEPT
# remote admin ssh and webmin
iptables -A INPUT -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -p tcp --dport 10000 -j ACCEPT
# ntop
iptables -A INPUT -i $_ethIN -p tcp --dport 3000 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3000 -j REJECT
# ftp
modprobe ip_conntrack_ftp
iptables -A INPUT -p TCP --dport 21 -m state --state NEW -j ACCEPT
iptables -A INPUT -p TCP --dport 20 -m state --state NEW -j ACCEPT
iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT
# rdp this server
iptables -A INPUT -i $_ethIN -p tcp --dport 3389 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3389 -j REJECT
# cifs and samba
iptables -A INPUT -p tcp -i eth0 --dport 137  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 138  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 139  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 389  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 445  -j ACCEPT
# ssh
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
# netperf 12865
iptables -A INPUT -p tcp --dport 12865 -j ACCEPT
# ServerMonitoring


################
#
# OUTPUT
#
################
echo "setting up OUTPUT"
iptables -A OUTPUT -j ACCEPT



###################
#
# FORWARD
#
##################
echo "setting up FORWARD"
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -j ACCEPT



##################
#
# Webmin DNATs
#
##################
echo "setting up Webmin DNATs"
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10001 -j DNAT --to 10.1.1.5:10000
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10003 -j DNAT --to 10.1.1.3:10000
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10006 -j DNAT --to 10.1.1.6:10000
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10007 -j DNAT --to 10.1.1.7:10000

##################
#
# tt_ServerMonitor
#
#################
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 65533 -j DNAT --to $_Win2k8Server:65533
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 65534 -j DNAT --to $_Win2k8Server:65534
iptables -A INPUT -d $_Win2k8Server -p tcp --dport 65534 -j ACCEPT
iptables -A OUTPUT -s $_Win2k8Server -p tcp --dport 65534 -j ACCEPT

iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 5500 -j DNAT --to $_Win2k8Server:5500

##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY
iptables -A INPUT -d $_RUNUO -p tcp --dport 2593 -j ACCEPT
iptables -A OUTPUT -s $_RUNUO -p tcp --dport 2593 -j ACCEPT



##########################
#
# RDP NATs
#
#########################
echo "setting up RDP DNAT"
# to windows server
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3387 -j DNAT --to $_Win2k8Server:3389
# to Player
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3386 -j DNAT --to $_Player:3389
# to VMhost broken
#iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3385 -j DNAT --to $_FTP:3389



##########################
#
# minecraft
#
#########################
echo "setting up RDP DNAT"
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 25565 -j DNAT --to 10.1.1.21:25565



######################
#
# Webserver DNAT
#
#######################
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -j DNAT --to 10.1.1.6:80
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 8080 -j DNAT --to 10.1.1.6:80
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 443 -j DNAT --to 10.1.1.6:443
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10022 -j DNAT --to 10.1.1.6:22


#####################
#
# OpenDNS DNAT OUTGOING
#
####################
echo "setting up OpenDNS prerouting (the trap)"
# Need to change the below line to --to $_myDNS:53 so that DNS traffic not from 
#  my DNS server gets bounced to my DNS server.
#iptables -t nat -A PREROUTING  -s 10.1.1.69 -p udp --dport 53 -j DNAT --to 8.8.8.8:53
#iptables -t nat -A PREROUTING  -s 10.1.1.69 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53
#iptables -t nat -A PREROUTING ! -s $_myDNS -p udp --dport 53 -j DNAT --to $_OpenDNS:53
#iptables -t nat -A PREROUTING ! -s $_myDNS -p tcp --dport 53 -j DNAT --to $_OpenDNS:53


###################
#
# Default settings end of chain and  rejects
#
## tighten this up later.
echo "setting up defaults for end of chains"
#iptables -A INPUT -i eth0 -j REJECT
iptables -A INPUT -i $_ethOUT -j REJECT
iptables -A INPUT -i $_ethIN -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT
```

Above is my iptables script. Everything seems to be working great, except runuo. Local network users connect just fine. Internet users have an issue. If I do some tshark-ing I can see the internet clients connect to my internal server. There is conversation exchanging. Then the conversation just stops. It feels like the ESTABLISHED,RELATED section of the script isn't applying to the runuo users. But it does for RDP etc.

Any ideas? Thanks!

---

### Post by Doug S on 2013-01-07
I have been looking at your iptables rule set for quite awhile, but now have run out of time. I would suggest changing this:```
##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY
iptables -A INPUT -d $_RUNUO -p tcp --dport 2593 -j ACCEPT
iptables -A OUTPUT -s $_RUNUO -p tcp --dport 2593 -j ACCEPT
```to this:```
##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
```There are some other odd things in your rule set, such as a conditional ACCEPT on FORWARD following by an unconditional ACCEPT. Anyway, in a few hours I'll make a more detailed reply.

---

### Post by Doug S on 2013-01-07
Some additional comments on your iptables script in-line below:
```

#!/bin/bash
######################
#
#  Settings up variables for the script
#
######################
echo "setting up variables"
_ethOUT=eth1
    #_ethOUT is DHCP from ISP (outgoing interface)
_ethIN=eth0
dhclient $_ethOUT
#echo $_ethOUT
#_ethIN is static 10.1.1.5 and 10.1.1.1 it is also the bridge for VMs
_GATEWAY=$(ifconfig $_ethOUT | grep -v inet6 | grep inet | cut -d : -f 2 | sed 's/Bcast//')
echo $_GATEWAY
echo "The gateway inteface is $_ethOUT and its IP is $_GATEWAY"
echo "The internal interface is $_ethIN"
_FTP=10.1.1.5
_RUNUO=10.1.1.7
_CYGNENOS=10.1.1.3
_myDNS=$_CYGNENOS
_myDHCP=$_CYGNNOS
_Win2k8Server=10.1.1.9
_OpenDNS=208.67.222.222
_Player=10.1.1.19
[COLOR=red]<<< For consistency, why not declare 10.1.1.21 and .6 here?[/COLOR]
 
########################
#
#   Flushing and setting defaults accepts
#
######################
echo "Flushing and setting defaults"
echo "  flush nat"
iptables -t nat -F
#iptables -P INPUT ACCEPT [COLOR=red]<<< Suggest uncomment and default to DROP (or REJECT)[/COLOR]
echo "  flush input"
iptables -F INPUT
echo "  flush nat prerouting"
iptables -t nat -F PREROUTING
echo "  flush nat postrouting"
iptables -t nat -F POSTROUTING
echo "  flush output"
iptables -F OUTPUT
iptables -P OUTPUT ACCEPT
echo "  flush forward"
iptables -F FORWARD
iptables -P FORWARD ACCEPT
##########################
#
# ICMP
#
##########################
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
 
################
#
# Masqurading
#
#################
echo "setting up masqurading"
# only need the one outgoing interface for internet access
iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE
 
################
#
# INPUT
#   - IN TO THIS SERVER
#
###############
echo "setting up INPUT"
# default states
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT[COLOR=red]   <<<< Notice[/COLOR]
# ntp from local server
iptables -A INPUT -p udp -i $_ethIN --dport 123 -j ACCEPT
# remote admin ssh and webmin
iptables -A INPUT -p tcp --dport ssh -j ACCEPT [COLOR=red]<<< SSH done here, and below[/COLOR]
iptables -A INPUT -p tcp --dport 10000 -j ACCEPT
# ntop
iptables -A INPUT -i $_ethIN -p tcp --dport 3000 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3000 -j REJECT
# ftp
modprobe ip_conntrack_ftp   [COLOR=red]<<< Not needed, kernel will load it if needed.[/COLOR]
iptables -A INPUT -p TCP --dport 21 -m state --state NEW -j ACCEPT
iptables -A INPUT -p TCP --dport 20 -m state --state NEW -j ACCEPT
iptables -A INPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT [COLOR=red]<<< Delete, already done above see "Notice"[/COLOR]
iptables -A OUTPUT -p ALL -m state --state ESTABLISHED,RELATED -j ACCEPT [COLOR=red]<<< Delete. Generally OUTPUT from the server itself is ACCEPTED[/COLOR]
# rdp this server
iptables -A INPUT -i $_ethIN -p tcp --dport 3389 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3389 -j REJECT
# cifs and samba
iptables -A INPUT -p tcp -i eth0 --dport 137  -j ACCEPT  [COLOR=red]<<< Inconsistent. Use $_ethIN[/COLOR]
iptables -A INPUT -p tcp -i eth0 --dport 138  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 139  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 389  -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 445  -j ACCEPT
# ssh
iptables -A INPUT -p tcp --dport 22 -j ACCEPT  [COLOR=red]<<< Delete, already done above[/COLOR]
# netperf 12865
iptables -A INPUT -p tcp --dport 12865 -j ACCEPT
# ServerMonitoring
 
################
#
# OUTPUT
#
################
echo "setting up OUTPUT"
iptables -A OUTPUT -j ACCEPT
 
###################
#
# FORWARD
#
##################
echo "setting up FORWARD"
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT [COLOR=red]<<< Delete[/COLOR]
iptables -A FORWARD -j ACCEPT  [COLOR=red]<<< Since you ACCEPT anyhow[/COLOR]
 
##################
#
# Webmin DNATs
#
##################
echo "setting up Webmin DNATs"
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10001 -j DNAT --to 10.1.1.5:10000[COLOR=red] << ?? use $_FTP[/COLOR]
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10003 -j DNAT --to 10.1.1.3:10000 [COLOR=red]<<...[/COLOR]
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10006 -j DNAT --to 10.1.1.6:10000
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10007 -j DNAT --to 10.1.1.7:10000
 
##################
#
# tt_ServerMonitor
#
#################
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 65533 -j DNAT --to $_Win2k8Server:65533
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 65534 -j DNAT --to $_Win2k8Server:65534
iptables -A INPUT -d $_Win2k8Server -p tcp --dport 65534 -j ACCEPT[COLOR=red] <<< Delete[/COLOR]
iptables -A OUTPUT -s $_Win2k8Server -p tcp --dport 65534 -j ACCEPT [COLOR=red]<<< Delete[/COLOR]
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 5500 -j DNAT --to $_Win2k8Server:5500
 
##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY[COLOR=red] <<< Delete[/COLOR]
iptables -A INPUT -d $_RUNUO -p tcp --dport 2593 -j ACCEPT [COLOR=red]<<< Delete[/COLOR]
iptables -A OUTPUT -s $_RUNUO -p tcp --dport 2593 -j ACCEPT [COLOR=red]<<< Delete[/COLOR]
 
##########################
#
# RDP NATs
#
#########################
echo "setting up RDP DNAT"
# to windows server
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3387 -j DNAT --to $_Win2k8Server:3389
# to Player
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3386 -j DNAT --to $_Player:3389
# to VMhost broken
#iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3385 -j DNAT --to $_FTP:3389
 
##########################
#
# minecraft
#
#########################
echo "setting up RDP DNAT"
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 25565 -j DNAT --to 10.1.1.21:25565
 
######################
#
# Webserver DNAT
#
#######################
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -j DNAT --to 10.1.1.6:80 [COLOR=red]<<< Inconsistent. Use $ethOUT and a something for 10.1.1.6[/COLOR]
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 8080 -j DNAT --to 10.1.1.6:80
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 443 -j DNAT --to 10.1.1.6:443
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 10022 -j DNAT --to 10.1.1.6:22
 
#####################
#
# OpenDNS DNAT OUTGOING
#
####################
echo "setting up OpenDNS prerouting (the trap)"
# Need to change the below line to --to $_myDNS:53 so that DNS traffic not from 
#  my DNS server gets bounced to my DNS server.
#iptables -t nat -A PREROUTING  -s 10.1.1.69 -p udp --dport 53 -j DNAT --to 8.8.8.8:53
#iptables -t nat -A PREROUTING  -s 10.1.1.69 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53
#iptables -t nat -A PREROUTING ! -s $_myDNS -p udp --dport 53 -j DNAT --to $_OpenDNS:53
#iptables -t nat -A PREROUTING ! -s $_myDNS -p tcp --dport 53 -j DNAT --to $_OpenDNS:53
 
###################
#
# Default settings end of chain and  rejects
#
## tighten this up later. [COLOR=red]<<< O.K.[/COLOR]
echo "setting up defaults for end of chains"
#iptables -A INPUT -i eth0 -j REJECT
iptables -A INPUT -i $_ethOUT -j REJECT
iptables -A INPUT -i $_ethIN -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT[COLOR=red]  <<< Done above, but maybe you will change to DROP or REJECT when tightened[/COLOR]

```There is very handy diagram [here]("http://bodhizazen.net/Tutorials/iptables/") that helps with following packet flow through the iptables. I always have a printed copy within reach.

---

### Post by chadk5utc on 2013-01-07
Ill second what DougS commented.

---

### Post by ant2ne on 2013-01-12
I did most of your suggestions
If I remove```
modprobe ip_conntrack_ftp
``` then FTP stops working

If I do this
```

##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
```
I can't connect to runuo at all. See what UO is doing is that I can connect, login, see my server name, but get disconnected instantly. Without that second line I can't even connect. 

I think I'm barking up the wrong tree and my iptables is mostly right and this is a networking issue in some other way. The iptables is the only thing that has changed recently though.

---

### Post by Doug S on 2013-01-12
Automatic modue loading: What version of ubuntu are you running? And is there any auto disable for the ip_coontrack_ftp module? Look in /etc/modprobe.d? Example:```
doug@doug-64:/etc/modprobe.d$ grep -i ftp *
doug@doug-64:/etc/modprobe.d$
```> [COLOR=#000000]Without that second line I can't even connect. [/COLOR]Do you mean this line?:```
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY

```I'll think about this some more, as I probably missed something. Myself, I don't use MASQUERADE, instead I use SNAT, so I might suggest to change this:```
iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE
```to this:```
iptables -t nat -A POSTROUTING -o $_ethOUT -j SNAT --to _GATEWAY
```
You are referring to exernal access correct? I assume that internal users connect directly to _RUNUO.

---

### Post by ant2ne on 2013-01-14
> **Doug S said:**
> Automatic modue loading: What version of ubuntu are you running? And is there any auto disable for the ip_coontrack_ftp module? Look in /etc/modprobe.d? Example:```
doug@doug-64:/etc/modprobe.d$ grep -i ftp *
doug@doug-64:/etc/modprobe.d$
```Do you mean this line?:```
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY

```I'll think about this some more, as I probably missed something. Myself, I don't use MASQUERADE, instead I use SNAT, so I might suggest to change this:```
iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE
```to this:```
iptables -t nat -A POSTROUTING -o $_ethOUT -j SNAT --to _GATEWAY
```
You are referring to exernal access correct? I assume that internal users connect directly to _RUNUO.


```
ant2ne@vmhost:/etc/modprobe.d$ grep -i ftp *
ant2ne@vmhost:/etc/modprobe.d$ 

```

> Do you mean this line?:

Yes, that is the line.

I changed it to ```
iptables -t nat -A POSTROUTING -o $_ethOUT -j SNAT --to $_GATEWAY
``` I will test it and report back.

---

### Post by Doug S on 2013-01-15
> I did most of your suggestions
If I remove 
Code:
modprobe ip_conntrack_ftp
then FTP stops working
Sorry, my mistake. I realize now there is no specific iptables rule that would cause the module to autoload, so it needs to be manually loaded.

---

### Post by ant2ne on 2013-01-16
no changes. still fails to maintain connection.

---

### Post by Doug S on 2013-01-19
Darn it. I wrote a reply a couple of days ago, but sometimes I hit "preview" instead of "submit"... Anyway....
 
Why is the runuo section different than the others? I can not figure out how a packet being returned from the server can get out to internet. I'm suggesting that an interface be specified in the prerouting rule, just like the others. I.E. should this line:```
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
```be this:```
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT --dport 2593 -j DNAT --to $_RUNUO:2593
```

---

### Post by ant2ne on 2013-01-21
i went back to this

```
##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport 2593 -j DNAT --to $_RUNUO:2593
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport 2593 -j SNAT --to-source $_GATEWAY

```except I changed the port to 88. I change the server to listen to 88. And it worked. I'm not sure what that is all about. Maybe my ISP started blocking 2593.

---

