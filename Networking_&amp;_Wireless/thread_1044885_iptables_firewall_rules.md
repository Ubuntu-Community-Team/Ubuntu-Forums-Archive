---
title: "iptables firewall rules"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Lupine on 2009-01-19
I have recently upgraded my BLFS box to Ubuntu 8.10.  Many years ago, I researched and wrote this iptables script that I have always used:

--------------------------------------------------------------------------------
#!/bin/sh

IPTABLES=`which iptables`
DEPMOD=`which depmod`
MODPROBE=`which modprobe`
GREP=`which grep`
AWK=`which awk`
SED=`which sed`
IFCONFIG=`which ifconfig`
EXTIF="eth0"   # Internet connection
EXTIP="`$IFCONFIG $EXTIF | $AWK  /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
INTIF="eth1"
INTIP="192.168.5.1/24"
INTNET="192.168.5.0/24"
UNIVERSE="0.0.0.0"

###################################################
# Load up iptables modules
#
$DEPMOD -a
$MODPROBE ip_tables
$MODPROBE iptable_filter
$MODPROBE ip_conntrack
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_conntrack_irc
$MODPROBE iptable_nat
$MODPROBE ip_nat_ftp
$MODPROBE ip_nat_irc
$MODPROBE ipt_state
$MODPROBE ipt_ULOG

###################################################
# Turn on IP-Forwarding and Dynamic-Addressing
#
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

###################################################
# Clearing any existing rules and setting default policy..
#
#first clear any settings
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -F -t nat
if [ -n "`$IPTABLES -L | $GREP drop-and-log-it`" ]; then
   $IPTABLES -F drop-and-log-it
fi
$IPTABLES -X
$IPTABLES -Z

###################################################
# DROPs: drop certain packets without logging or anything
#

# ICMP stuff
$IPTABLES -A INPUT -i $EXTIF -p icmp -j DROP


# DROP without logging stuff that I really don't care about....Micr$not's SMB probes...etc.
$IPTABLES -A INPUT -i $EXTIF -p udp -d $EXTIP --dport 135:139 -j DROP	#M$
$IPTABLES -A INPUT -i $EXTIF -p udp -d $EXTIP --dport 445 -j DROP	#M$
$IPTABLES -A INPUT -i $EXTIF -p udp -d $EXTIP --dport 1434 -j DROP	#M$
$IPTABLES -A INPUT -i $EXTIF -p udp -d $EXTIP --dport 1025:1027 -j DROP	#M$
$IPTABLES -A INPUT -i $EXTIF -p tcp -d $EXTIP --dport 21 -j DROP	#FTP
$IPTABLES -A INPUT -i $EXTIF -p tcp -d $EXTIP --dport 53 -j DROP	#DNS


###################################################
# Create DROP and LOG chaning
#
$IPTABLES -N drop-and-log-it
$IPTABLES -A drop-and-log-it -d $EXTIP -j ULOG --ulog-nlgroup 1 --ulog-prefix "FIREWALL: "
#$IPTABLES -A drop-and-log-it -d $EXTIP -j LOG --log-prefix "FIREWALL: "
$IPTABLES -A drop-and-log-it -j DROP

###################################################
# INPUT: Incoming traffic from various interfaces.  
# All rulesets are already flushed and set to a default policy of DROP. 
#

# loopback interfaces are valid.
$IPTABLES -A INPUT -i lo -j ACCEPT


# allow internal networks
$IPTABLES -A INPUT -s $INTNET -j ACCEPT

# remote interface, claiming to be local machines, IP spoofing, get lost
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j drop-and-log-it

# allow already established connections and permit new related connections
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# catch all rule, all other incoming is denied and logged. 
$IPTABLES -A INPUT -j drop-and-log-it


###################################################
# OUTPUT: Outgoing traffic from various interfaces.
#        All rulesets are already flushed and set to a default policy of DROP. 
#

# loopback interface is valid.
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# local interface, any source going to local net is valid
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT

# outgoing to local net on remote interface, stuffed routing, deny
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j drop-and-log-it

# anything outgoing on remote interface is valid
$IPTABLES -A OUTPUT -j ACCEPT

# Catch all rule, all other outgoing is denied and logged. 
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it


###################################################
# FORWARD: Enable Forwarding and thus IPMASQ
# All rulesets are already flushed and set to a default policy of DROP. 
#

# Allow all connections OUT and only existing/related IN
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED  -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch all rule, all other forwarding is denied and logged. 
$IPTABLES -A FORWARD -j drop-and-log-it

# Enabling SNAT (MASQUERADE) functionality on $EXTIF
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
--------------------------------------------------------------------------------

Everything loads up fine, and I see no errors, however none of my Internal desktop/laptops can access the Internet.  Well, they can ping/resolve addresses, but they can't surf the web, connect to IRC, connect to IM...etc.  I have tried everything, but can not seem to get this script to work on Ubuntu 8.10, whereas it worked perfectly fine on BLFS.  To make sure Ubuntu 8.10 was otherwise working, I installed firestarter, and that did work.  However, I would rather use my old reliable script above.  Thoughts as to why this isn't working on Ubuntu?

Thanks,
-Lup

---

### Post by Lupine on 2009-01-20
Further troubleshooting hasn't helped me much.  I've taken the above script, Googled around for a while and simplified it to this script:

--------------------------------------------------------------------------------
#!/bin/sh

IPTABLES=`which iptables`
DEPMOD=`which depmod`
MODPROBE=`which modprobe`
GREP=`which grep`
AWK=`which awk`
SED=`which sed`
IFCONFIG=`which ifconfig`
EXTIF="eth0" # Internet connection
EXTIP="`$IFCONFIG $EXTIF | $AWK /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"
INTIF="eth1"
INTIP="192.168.5.1/24"
INTNET="192.168.5.0/24"
UNIVERSE="0.0.0.0"

################################################## #
# Load up iptables modules
#
$DEPMOD -a
$MODPROBE ip_tables
$MODPROBE iptable_filter
$MODPROBE ip_conntrack
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_conntrack_irc
$MODPROBE iptable_nat
$MODPROBE ip_nat_ftp
$MODPROBE ip_nat_irc
$MODPROBE ipt_state
$MODPROBE ipt_ULOG

################################################## #
# Turn on IP-Forwarding and Dynamic-Addressing
#
echo "1" > /proc/sys/net/ipv4/ip_forward
$IPTABLES -P FORWARD ACCEPT
$IPTABLES --table nat -A POSTROUTING -o $EXTIF -j MASQUERADE
--------------------------------------------------------------------------------


Stop and restarted my firewall script, but still no go.  Obviously, I'm just trying to simplify the script down to the "minimum" for NAT (IP forwarding)...but even this simplified version isn't working :(

I must be missing something simple, but I just can't figure out what.  Any suggestions?

---

### Post by Lupine on 2009-01-20
I've re-read over the following Router documentation:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

...but it is still no go.  I altered my script to that documentation (minus the bridging stuff br0 == eth1), however it still fails to allow internal devices to surf the web, connect to IRC...etc.  The server itself can access all these services just fine, but not the LAN connected devices.

So weird!

---

### Post by kevdog on 2009-01-20
Does it work with the iptables turned off and flushed?  Meaning can you connect and browse the internet


If so, what does this line resolve to?:
$IPTABLES --table nat -A POSTROUTING -o $EXTIF -j MASQUERADE

---

### Post by Lupine on 2009-01-20
If I flush and shut off iptables, the server itself can still browse/IRC/IM...however, none of the internal PCs can.  In fact, the internal PCs can not even ping [www.ubuntu.com](www.ubuntu.com).

However, if I turn my firewall/iptables back on....server is still fine, internal PCs can now ping [www.ubuntu.com](www.ubuntu.com), but internal PCs can't browse/IRC/IM/etc.  Does that answer your question?


As for "what does this line resolve to"...I'm not sure what you are asking there.  Please let me know if there is any other infor I can provide, I really (REALLY) appreciate your time.

This almost feels like Ubuntu, unlike my older BLFS/kernel, requires 1.) another ipt_* module loaded? or 2.) another "echo 1 > /proc/sys/net/ipv4/something" done.

Thanks again for your help, and any other light you can shed on this.
-Lup

---

### Post by jallot on 2009-01-21
> **Lupine said:**
> If I flush and shut off iptables, the server itself can still browse/IRC/IM...however, none of the internal PCs can.  In fact, the internal PCs can not even ping [www.ubuntu.com](www.ubuntu.com).

However, if I turn my firewall/iptables back on....server is still fine, internal PCs can now ping [www.ubuntu.com](www.ubuntu.com), but internal PCs can't browse/IRC/IM/etc.  Does that answer your question?


As for "what does this line resolve to"...I'm not sure what you are asking there.  Please let me know if there is any other infor I can provide, I really (REALLY) appreciate your time.

This almost feels like Ubuntu, unlike my older BLFS/kernel, requires 1.) another ipt_* module loaded? or 2.) another "echo 1 > /proc/sys/net/ipv4/something" done.

Thanks again for your help, and any other light you can shed on this.
-Lup

I encountered the same problem when I upgraded to 8.10 yeserday. LAN side PCs can ping internet destinations but cannot surf the web.  Web surfing on the server works fine. My Iptables script worked properly in 8.04 but does not in 8.10.   I am somewhat surprised that others have not encountered the same problem with 8.10.

---

### Post by Lupine on 2009-01-21
jallot,

Thx so much for your reply.  It's nice to know that I'm not alone.  Hopefully someone out there knows about this, and can do something about it.  Each night when I get home from work, I Google around some more, post in the IRC channels, try altering my script..etc.  I'm determined to get this solved.  But so for no luck.

Thanks again,
-Lup

---

### Post by docawk on 2009-01-21
Did you check the routing table?

Post the output of the following commands:

```
ip route list
ip rule list
```

---

### Post by Lupine on 2009-01-21
Thanks, here are the results from the server:

$> ip route list
192.168.5.0/24 dev eth1  proto kernel  scope link  src 192.168.5.1 
70.121.168.0/21 dev eth0  proto kernel  scope link  src 70.121.175.4 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 70.121.168.1 dev eth0  metric 100 


$> ip rule list
0:	from all lookup local 
32766:	from all lookup main 
32767:	from all lookup default 


And here are the results from the client:
$> ip route list
192.168.5.0/24 dev eth0  proto kernel  scope link  src 192.168.5.10 metric 1
default via 192.168.5.1 dev eth0 proto static


$> ip rule list
0:	from all lookup local 
32766:	from all lookup main 
32767:	from all lookup default 


See anything that looks incorrect?  192.168.5.10 is the DHCP assigned address to my workstation...it's the one I've always used.

Thanks,
-Lup

---

### Post by docawk on 2009-01-21
No that looks fine to me. Should work from the routing point of view.
One thing I don't see the reason for, but should not causing any problem is the route:
169.254.0.0/16 dev eth0 scope link metric 1000

---

### Post by Lupine on 2009-01-21
True, I noticed that too...and not sure where it's coming from.  Weird how it's only showing up on the server, and not the clients.  I was thinking it was something to do with avahi.  Might have to research that a little more.

I tried a few more tests.  First, I installed iptstate so I could watch the connections in real time.  Then, on my 192.168.5.10 workstation, I tried to first ping [www.ubuntu.com](www.ubuntu.com)

192.168.5.10:58614                                               192.168.5.1:53                                                   udp                 0:00:16
192.168.5.10:41532                                               192.168.5.1:53                                                   udp                 0:00:20
192.168.5.10:36659                                               192.168.5.1:53                                                   udp                 0:00:16
192.168.5.10:35905                                               192.168.5.1:53                                                   udp                 0:00:17
192.168.5.10:43509                                               192.168.5.1:53                                                   udp                 0:00:23

...I saw these grow and grow, which makes sense, as my client (192.168.5.10) was using my server(192.168.5.1), which is also my DNS/DHCP server to resolve this name and respond.  So, I then tried to ping 91.189.94.8 (the ip of [www.ubuntu.com](www.ubuntu.com)), and I saw no changes in iptstate.  Interesting?

Next, I tried to traceroute to 91.189.94.8, and saw this:

192.168.5.10:40787                                               91.189.94.8:33447                                                udp                 0:00:21
192.168.5.10:47569                                               91.189.94.8:33459                                                udp                 0:00:26
192.168.5.10:35940                                               192.168.5.1:53                                                   udp                 0:00:26
192.168.5.10:56885                                               91.189.94.8:33441                                                udp                 0:00:21
192.168.5.10:35019                                               91.189.94.8:33498                                                udp                 0:00:27
192.168.5.10:55902                                               91.189.94.8:33484                                                udp                 0:00:26
192.168.5.10:46365                                               91.189.94.8:33458                                                udp                 0:00:26
192.168.5.10:49755                                               91.189.94.8:33443                                                udp                 0:00:21
192.168.5.10:43907                                               91.189.94.8:33488                                                udp                 0:00:27

...ok, there's some traffic to Ubuntu.

Finally, I launched FireFox and went to [www.ubuntu.com](www.ubuntu.com), and saw this:
192.168.5.10:37210                                               91.189.94.8:80                                                   tcp   ESTABLISHED 119:59:47
192.168.5.10:53919                                               192.168.5.1:53                                                   udp                 0:00:17

Hmmmm, weird.  The 192.168.5.1:53 was the DNS request to my server to resolve the name, makes sense, but the other line has me puzzled.  If it thinks that I've "ESTABLISHED" a connection from 192.168.5.10 to 91.189.94.8:80....then why isn't my client seeing the page?

Going to keep digging.
-Lup

---

### Post by oooh on 2009-01-23
Same problem here

Hardy 8.10. Static IP addresses

I also have this:

169.254.0.0/16 dev eth0 scope link metric 1000

In my route table. 

In addition to that, the only weird thing I could find so far was the 
/etc/network/interfaces , that is FULL of empty lines, and though has:
auto lo 
and 
auto eth0

The auto eth0 goes to the end of the file everytime I restart network, even if I fix and clean the file manually in root.

> **docawk said:**
> No that looks fine to me. Should work from the routing point of view.
One thing I don't see the reason for, but should not causing any problem is the route:
169.254.0.0/16 dev eth0 scope link metric 1000

---

### Post by Lupine on 2009-01-23
Thx for the confirmation oooh, that is now 3 of us having the exact same problem.  Looks like I might need to open a BugReport on this...I searched around, and didn't see anything already opened.

For what it's worth, here is my /etc/network/interfaces file looks like:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address         192.168.5.1
        netmask         255.255.255.0
        broadcast       192.168.5.255
        network         192.168.0.0
..and if I restart networking, it stays the same.

Thx,
-Lup

---

### Post by oooh on 2009-01-23
I think i will try to go to the default ubuntu network settings and start all over again, so maybe the route table is cleaned up completelly.

rm -fR .gconf/system/networking/connections

:S

When I have some news I ll tell you all

---

### Post by Lupine on 2009-01-24
Well, I thought I would give Ubuntu 8.10 Server Edition a try, since the documentation here: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) states that it was all done using Ubuntu Server.

Just got done installing Ubuntu Server and all it's updates, loaded up DHCP/DNS services and then my firewall script...but still no luck.

I'm at a loss...I have no idea what to try next.

---

### Post by Lupine on 2009-01-24
jallot or oooh,

Could one of you two please go here: [https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/320899](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/320899) and post that you can confirm this bug is happening to you too and then mark the bug as Confirmed.  This might help get some help with our issues.

Thanks,
-Lup

---

### Post by Xamiga on 2009-01-24
Have you removed NetworkManager and firestarter and then tested your script?

---

### Post by Lupine on 2009-01-24
Yes, in fact with Ubuntu Server, there is no NetworkManager.  I've also disabled ufw and apparmor.

The current setup I have now, is a freshly installed Ubuntu Server 8.10 box, with the bare minimum for DNS/DHCP and my script.  All other services are either not installed or disabled.

Thanks,
-Lup

---

### Post by Lupine on 2009-01-25
Wanted to share a little more info and confirmation on what I have discovered.

I booted off one of my old Ubuntu Hardy Desktop CDs, mounted the Interpid hard drive so I could get to my scripts and configs.  Installed DNS/DHCP services, copied over my configs, loaded everything up including my firewall script and everything works!!!

So, this is simply a matter of something is different in Intrepid, as it does work perfectly fine in Hardy.

---

### Post by Lupine on 2009-01-26
Further updates:


It works perfectly fine in Jaunty...so looks like we all just need to upgrade :-)

---

### Post by oooh on 2009-01-26
ok , weirdest thing ever 

now it works 

i did nothing but not use the laptop for the weekend

i posted more details about my status here:

[http://ubuntuforums.org/showthread.php?p=6622709#post6622709](http://ubuntuforums.org/showthread.php?p=6622709#post6622709)

i think it was something related to the firewall either firestarter or iptable directly

---

