---
title: "SSH issue (IPtables)"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by qwertyface on 2011-06-25
Hi all,

I've been making use of the resources available regarding iptables, mainly:

[LIST]
[*][I][http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)
[*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[/I]
[/LIST]

From various forums that people have posted to, I have seen their scripts and learned from them too, etc. So I think I'm getting to grips in understand the basics of iptables now.

However, one solution to an issue that I am having with allowing incoming SSH connections is still eluding me.

It would be terrific is you could help me trouble-shoot this. Here's my script:

**== EDIT! ==**
My version of iptables is 1.4.11.1

```

#! /bin/bash
#
# Configuring of IPTABLES to define the connection rules
#
# The default POLICY == DROP, thus all following
# rules will be to ACCEPT specific traffic.
#

# set interface strings 
WLAN="wlan+"
TAP="tap+"

# clear current rules and chains
iptables -F
iptables -X

# set default policy to drop
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

# Load some modules that may need.
#modprobe ip_tables
#modprobe ip_nat_ftp
#modprobe ip_nat_irc
#modprobe iptable_filter
#modprobe iptable_nat 
#modprobe ip_conntrack_irc
#modprobe ip_conntrack_ftp
modprobe ip_conntrack
modprobe ipt_LOG

# accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# accept input/output on loopback interface
iptables -A INPUT -i lo -p all -j ACCEPT
iptables -A OUTPUT -o lo -p all -j ACCEPT

# Allow ICMP requests/replies
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT  -p icmp --icmp-type echo-reply -j ACCEPT

# Allow incoming SSH connections, but only from inside the LAN
# and log them.
iptables -A INPUT -i $WLAN -p tcp --dport 22 -s 192.168.2.0/24 -j LOG --log-prefix '** INCOMING SSH FROM LAN **' --log-level 4
iptables -A INPUT -i $WLAN -p tcp --dport 22 -s 192.168.2.0/24 -j ACCEPT

# Allow incoming SSH connections, but only from work network
# and log them.
iptables -A INPUT -i $WLAN -p tcp --dport 22 -s [work's n/w] -j LOG --log-prefix '** INCOMING SSH FROM WORK **' --log-level 4
iptables -A INPUT -i $WLAN -p tcp --dport 22 -s {work's n/w] -j ACCEPT

# Allow outgoing SSH connections, but destined only the LAN
# and log them.
iptables -A OUTPUT -o $WLAN -p tcp --dport 22 -d 192.168.2.0/24 -j LOG --log-prefix '** OUTGOING SSH INSIDE LAN **' --log-level 4
iptables -A OUTPUT -o $WLAN -p tcp --dport 22 -d 192.168.2.0/24 -j ACCEPT

# open main operational ports to be functional, plus those for VPN
# for TAP to connect through.
iptables -A OUTPUT -o $WLAN -p tcp --dport 80 -j ACCEPT #HTTP
iptables -A OUTPUT -o $WLAN -p tcp --dport 443 -j ACCEPT #HTTPS
iptables -A OUTPUT -o $WLAN -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -o $WLAN -p udp --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -o $WLAN -p udp --dport 1194 -j ACCEPT #openvpn
iptables -A OUTPUT -o $WLAN -p udp --dport 10010 -j ACCEPT #openvpn
iptables -A OUTPUT -o $WLAN -p udp --dport 10020 -j ACCEPT #openvpn

# open same ports on TAP interface too.
# iptables -A OUTPUT -o $TAP -p udp --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -o $TAP -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -o $TAP -p tcp --dport 80 -j ACCEPT #http
iptables -A OUTPUT -o $TAP -p tcp --dport 443 -j ACCEPT #https
iptables -A OUTPUT -o $TAP -p tcp --dport 22 -j ACCEPT #ssh
iptables -A OUTPUT -o $TAP -p tcp --dport 20:21 -j ACCEPT #ftp
iptables -A OUTPUT -o $TAP -p tcp --dport 6881:6889 -j ACCEPT #bit torrent

# explicitly drop everything that has not been previously allowed
iptables -A FORWARD -j DROP
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

```

What I find is that the first TCP SYN packet comes through, but my machine does not respond with a SYN/ACK packet as shown in the following Wireshark screen print:

[IMG]http://img853.imageshack.us/img853/3489/ssh.png[/IMG]

I have no idea why this is?

Also, another question I have is what modules to load? Are they necessary on a client, i.e. I gather the **iptable_nat** module isn't required for a client machine but rather only if I was writing a script for my DD-WRT router, right?...

Would somebody shed light onto what modules are most pertinent for a client and for a server, please?

Now, this is not related to an issue I am having it's more something I've noticed but why is there a DNS request for an address related to *.ARPA directly after I type:

```
#iptables -L
```

Here's a screen print:

[IMG]http://img30.imageshack.us/img30/7743/arpa.png[/IMG]

BTW, I reckon that a great way to understand iptables would be to be able to visualise it so if you know of any links where I can visualise what's going on please link it, i.e. a diagram or something (but not that one on the first link when I started!).

As per usual, many thanks for your input(s) in advance!

:D

---

### Post by Dangertux on 2011-06-26
From what I can see your script looks decent. This might seem like a no brainer kinda thing, but are you using ufw as well? Because ufw can munge your iptables rules if you're not careful with how you're implementing them.

EDIT : If that's not the case you might consider something like this. That might help.

iptables -A INPUT -i $WLAN -p tcp --dport 22 -s 192.168.2.0/24 -m state --state NEW -j ACCEPT

---

### Post by qwertyface on 2011-06-26
Hi Dangertux,

Thanks for your reply.

> **Dangertux said:**
> ...This might seem like a no brainer kinda thing, but are you using ufw as well?

No, I am not using ufw. I did previously have Firestarter installed, however I removed that about 3 days ago with:

```
#sudo apt-get remove firestarter
```

Having said that, the old Firestarter folder at /etc/firestarter and its contents are still all their. Would this be an issue? (If it is, why was the above command not sufficient?)

I have noticed that in the Ubuntu HowTo on iptables it does mention that NetworkManager is an issue:

[LIST]
[*][https://help.ubuntu.com/community/IptablesHowTo#Configuration on startup]("https://help.ubuntu.com/community/IptablesHowTo#Configuration on startup")
[/LIST]

Do you know if this is still an issue with Ubuntu Maverick?

Also, I tried the following:

> **Dangertux said:**
> iptables -A INPUT -i $WLAN -p tcp --dport 22 -s 192.168.2.0/24 -m state --state NEW -j ACCEPT

But this does not change anything. Thanks anyway though.

---

### Post by gmargo on 2011-06-26
> 
why is there a DNS request for an address related to  *.ARPA directly after I type: iptables -L
**iptables(8)** is attempting to do a reverse DNS lookup to find the hostname of your local IP addresses.  Use the "-n" (or "--numeric") option to avoid the lookups, which will really speed up the command.

> 
BTW, I reckon that a great way to understand iptables would be to be  able to visualise it so if you know of any links where I can visualise  what's going on please link it, i.e. a diagram or something (but not  that one on the first link when I started!).
I rather like the image with the Wikipedia article: [http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

---

### Post by gmargo on 2011-06-26
> 
a diagram
Once upon a time, I wrote my own firewall script.  Here for your enjoyment is a portion of that script: a text version of the packet traversal.
```

#################################################
#
#  How packets traverse the tables/chains.
#
# Ascii-ized version of much nicer picture in tutorial:
#
#
#                      Network
#                        |
#                        v
#                      raw
#                      PREROUTING
#                        |
#                        v
#                      mangle
#                      PREROUTING
#                        |
#                        v
#                      nat
#                      PREROUTING
#                        |
#                        v
#                      routing
#          +---------- decision -----------+
#          |                               |
#          v                               v
#        mangle                          mangle
#        INPUT                           FORWARD
#          |                               |
#          v                               v
#        filter                          filter
#        INPUT                           FORWARD
#          |                               |
#          v                               |
#        local                             |
#        process                           |
#          |                               |
#          v                               |
#        routing                           |
#        decision                          |
#          |                               |
#          v                               |
#        raw                               |
#        OUTPUT                            |
#          |                               |
#          v                               |
#        mangle                            |
#        OUTPUT                            |
#          |                               |
#          v                               |
#        nat                               |
#        OUTPUT                            |
#          |                               |
#          v                               |
#        filter                            |
#        OUTPUT                            |
#          |                               |
#          v                               v
#          +---------> routing <-----------+
#                      decision
#                        |
#                        v
#                      mangle
#                      POSTROUTING
#                        |
#                        v
#                      nat
#                      POSTROUTING
#                        |
#                        v
#                      Network
#
#################################################

```

---

### Post by Dangertux on 2011-06-26
> **qwertyface said:**
> 
I have noticed that in the Ubuntu HowTo on iptables it does mention that NetworkManager is an issue:

[LIST]
[*][https://help.ubuntu.com/community/IptablesHowTo#Configuration on startup]("https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup")
[/LIST]


I am not in a position to test this at the moment, but I suspect it could be your problem.

---

### Post by gmargo on 2011-06-26
Do you have an **eth0** interface as well?  
Do those ip addresses from the Wireshark capture come from WLAN or TAP or eth0?  
With no iptables rules for eth0, they would be dropped.

---

### Post by Doug S on 2011-06-26
Hi,
I only have the server edition, so don't know about NetworkManager or any potential conflicts. 
You can prevent the DNS lookups for your "iptables &#8211;L" with an additional switch "iptables &#8211;L &#8211;x". Myself, I always use these switches "iptables &#8211;v -x &#8211;n &#8211;L", and would very much like to see the output from your machine to observe, via the counters, if your rules are being traversed. Similarly, do you see the log entries in /var/log/syslog with [COLOR=black]** INCOMING SSH FROM LAN **? This information will help us to know if I am on the right or wrong track with the below paragraph.[/COLOR]
[COLOR=black]It is not clear to me what is going on with your FORWARD chain. I think that it should be set to a default policy of ACCEPT, and should not have the separate line near the end specifically dropping any packets that got that far. Why? Because you are not doing anything in the forward chain and the INPUT and OUTPUT chains are taking care of your security. Alternatively, you could specifically allow incoming related and established traffic and all outgoing traffic through the FORWARD chain.[/COLOR]
 
[EDIT] I am pretty sure that what I said above about the "FORWARD" chain is incorrect. I went to my old old Ubuntu server, which has only one NIC (my newer server has two NICs and does routing). I see that on that machine that no packets ever go through the FORWARD chain, so it's setting don't matter. Sorry for any confusion.

---

### Post by qwertyface on 2011-06-26
Hi all,

Again, cheers for your contributions here.

> **gmargo said:**
> Do you have an **eth0** interface as well?

Yes, but I do not use it. My machine is only communicating to the router via wlan0. 

> **gmargo said:**
> Do those ip addresses from the Wireshark capture come from WLAN or TAP or eth0?

Both screen shots are from the wlan0 interface, when my VPN is disconnected (and tap0 is not active).

I did this because I want to test local LAN SSH connections coming into the machine, via wlan0.

> **gmargo said:**
> With no iptables rules for eth0, they would be dropped.

I understand this.

> **Doug S said:**
> ...You can prevent the DNS lookups for your "iptables –L" with an additional switch "iptables –L –x". Myself, I always use these switches "iptables –v -x –n –L", and would very much like to see the output from your machine to observe, via the counters, if your rules are being traversed.

Thanks, I'll do that in future. Here you go:

[[IMG]http://img861.imageshack.us/img861/255/ipt5465.th.png[/IMG]](http://img861.imageshack.us/i/ipt5465.png/)

> **Doug S said:**
>  Similarly, do you see the log entries in /var/log/syslog with [COLOR=black]** INCOMING SSH FROM LAN **? This information will help us to know if I am on the right or wrong track with the below paragraph.[/COLOR]

Yes, I do see that in the log. Here's some TCP SYN packets again:

[IMG]http://img864.imageshack.us/img864/8014/ssh5656g.png[/IMG] 

And a screen shot of the syslog log with said prefix:

[[IMG]http://img12.imageshack.us/img12/32/sysl6765.th.png[/IMG]](http://img12.imageshack.us/i/sysl6765.png/)

> **Doug S said:**
> [COLOR=black][EDIT] I am pretty sure that what I said above about the "FORWARD" chain is incorrect. I went to my old old Ubuntu server, which has only one NIC (my newer server has two NICs and does routing). I see that on that machine that no packets ever go through the FORWARD chain, so it's setting don't matter. Sorry for any confusion.[/COLOR]

OK, no worries.

---

### Post by Doug S on 2011-06-26
Hi,
 
I am running your iptables, with modifications for my network, on my old old Ubuntu server box. And yes, SSH is not working. There is no return path for response packets. For example, in your latest posting, there is no way for a packet from port 22 destined for port 54058 to get ACCEPTed in the OUTPUT chain, so the packet gets dropped by the OUTPUT rules catch all at the end.
I hope what I said makes sense, as I am out of time for just now. I can check my conclusion and do a more thorough posting later (maybe in a about 3-4 hours).

---

### Post by Dangertux on 2011-06-26
> **Doug S said:**
> Hi,
 
I am running your iptables, with modifications for my network, on my old old Ubuntu server box. And yes, SSH is not working. There is no return path for response packets. For example, in your latest posting, there is no way for a packet from port 22 destined for port 54058 to get ACCEPTed in the OUTPUT chain, so the packet gets dropped by the OUTPUT rules catch all at the end.
I hope what I said makes sense, as I am out of time for just now. I can check my conclusion and do a more thorough posting later (maybe in a about 3-4 hours).

Oh hey, Doug S is absolutely correct. 

```

# explicitly drop everything that has not been previously allowed
iptables -A FORWARD -j DROP
iptables -A INPUT -j DROP 
iptables -A OUTPUT -j DROP <--- Default Drop all Output unless previously defined above (which unprivilaged ports are not referenced in at all.)

```There is a similar rule at the beginning of the script as well. Usually unless you are very restrictive in your policies you would not limit unprivilaged ports in that manner (>1024). So you may wish to append that to your rules, or just remove the OUTPUT DROP policies. 

You may wish to add something like this
```

iptables -A OUTPUT -o $TAP -p tcp --dport 1025:65565 -j ACCEPT #OUTPUT on unprivilaged ports
iptables -A OUTPUT -o $WLAN -p tcp --dport 1025:65565 -j ACCEPT #OUTPUT on unprivilaged ports

```

Very nice catch Doug S :-) Make sure you give Doug S  credit for this one, not tryna snipe his discovery in the slightest bit, just trying to provide clarification for the OP in the interim.

---

### Post by Doug S on 2011-06-27
Hi,
 
The reason I did a hurried, somewhat incomplete, post earlier was that I saw that qwertyface was still on-line. However, by the time I finished writting the post qwertyface was off-line.
 
Dangertux: Thanks for stepping in and comfirming my findings. It saved me some time when I came back to it.
 
I have now made an edit to my version of the qwertface iptables script and SSH access is working fine. I did it a little different than was suggested by Dangertux. I did this (added the OUTPUT line):
```
 
# accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```
and here is my output for "iptables -v -n -x -L"
```
 
doug@test-smy:~$ sudo iptables -v -x -n -L
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    1007    48956 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0
       1       52 LOG        tcp  --  eth0   *       192.168.111.0/24     0.0.0.0/0           tcp dpt:22 LOG flags 0 level 4 prefix `** INCOMING SSH FROM LAN **'
       1       52 ACCEPT     tcp  --  eth0   *       192.168.111.0/24     0.0.0.0/0           tcp dpt:22
       2       56 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    1824   250047 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 LOG        tcp  --  *      eth0    0.0.0.0/0            192.168.111.0/24    tcp dpt:22 LOG flags 0 level 4 prefix `** OUTGOING SSH INSIDE LAN **'
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            192.168.111.0/24    tcp dpt:22
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           tcp dpt:80
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           tcp dpt:443
       1       74 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:53
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:1194
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:10010
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:10020
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
 

```

---

### Post by Dangertux on 2011-06-27
> **Doug S said:**
> Hi,
 
The reason I did a hurried, somewhat incomplete, post earlier was that I saw that qwertyface was still on-line. However, by the time I finished writting the post qwertyface was off-line.
 
Dangertux: Thanks for stepping in and comfirming my findings. It saved me some time when I came back to it.
 
I have now made an edit to my version of the qwertface iptables script and SSH access is working fine. I did it a little different than was suggested by Dangertux. I did this (added the OUTPUT line):
```
 
# accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```and here is my output for "iptables -v -n -x -L"
```
 
doug@test-smy:~$ sudo iptables -v -x -n -L
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    1007    48956 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0
       1       52 LOG        tcp  --  eth0   *       192.168.111.0/24     0.0.0.0/0           tcp dpt:22 LOG flags 0 level 4 prefix `** INCOMING SSH FROM LAN **'
       1       52 ACCEPT     tcp  --  eth0   *       192.168.111.0/24     0.0.0.0/0           tcp dpt:22
       2       56 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    1824   250047 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 LOG        tcp  --  *      eth0    0.0.0.0/0            192.168.111.0/24    tcp dpt:22 LOG flags 0 level 4 prefix `** OUTGOING SSH INSIDE LAN **'
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            192.168.111.0/24    tcp dpt:22
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           tcp dpt:80
       0        0 ACCEPT     tcp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           tcp dpt:443
       1       74 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:53
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpts:67:68
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:1194
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:10010
       0        0 ACCEPT     udp  --  *      eth0    0.0.0.0/0            0.0.0.0/0           udp dpt:10020
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
 

```

Nice -- That's actually the more appropriate way to do what I said. The way I said was...Not preferable for production, but better for testing purposes. I would use this method for finalization of the script.

Nice job :-)

---

### Post by Doug S on 2011-06-27
I forgot to comment on this:
>  
Also, another question I have is what modules to load? Are they necessary on a client, i.e. I gather the **iptable_nat** module isn't required for a client machine but rather only if I was writing a script for my DD-WRT router, right?...
 
Would somebody shed light onto what modules are most pertinent for a client and for a server, please?
 

You don't actually have to worry about it, particularly on a non-router machine. On my version of your script I commented out the module loads. The system will automatically loads what it needs.
One other point, that is just my personal preference: When I am debugging iptables scripts I like to reset the counters when I re-load, so I also added a line to the flushing area of the script:
```
# clear current rules and chains
iptables -F
iptables -X
# DougS: I want to reset the counters also.
iptables -Z

```

---

### Post by qwertyface on 2011-06-27
> **Dangertux said:**
> Oh hey, Doug S is absolutely correct. 

Very nice catch Doug S :-) Make sure you give Doug S credit for this one, not tryna snipe his discovery in the slightest bit, just trying to provide clarification for the OP in the interim.

Cheers for your contribution too! And of course I will give credit where it's due. :)

> **Doug S said:**
> Hi,
 
The reason I did a hurried, somewhat incomplete, post earlier was that I saw that qwertyface was still on-line. However, by the time I finished writing the post qwertyface was off-line.
 
Yeah, the reason I was online was because I saw your post and thought: "he's got it." 

However, I don't think I'm out of the woods just yet as incoming SSH is still proving to be somewhat finicky.

I knew there was an issue at the second stage of the 3-way handshake for inbound TCP connections (which the SSH protocol implements, as you know).

So the problem I was observing in Wireshark seemed to be:

===============================================================
Test machine (port :*n*) -------------SYN (SSH)-----------> Main machine (port: 22)
===============================================================

But no returning SYN ACK packet from my Main machine (which this iptables script is for).

Having now implemented the following:

> **Doug S said:**
> 

```
 
# accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

Also, where you said:

> **Doug S said:**
> On my version of your script I commented out the module loads. The system will automatically loads what it needs.

Cheers for answering that part of my original post.

> **Doug S said:**
> One other point... reset the counters:
```
iptables -Z

```

I also agree that that's a good idea. This is now included in my script. Brill.

After having now run the new script I get an RST ACK packet back, closing the request. As also shown by the following Wireshark dump:

[IMG]http://img190.imageshack.us/img190/1448/rstssh45.png[/IMG]

But you're claiming that this works for you (I am not disputing that BTW!) so I thought I'd investigate further. I think that my main machine is the problem not the new iptables script.

For test purposes I'll do a before and after with my secondary machine. Both machines are running **iptables v.1.4.11.1**, however my secondary machine is not Ubuntu 11.04. It's 10.10.

192.168.2.4 is my main machine that I am having the incoming SSH trouble with. 192.168.2.6 is my secondary machine.

Before executing the iptables script on my secondary machine, my iptables -vnx -L output was as follows:

```

Chain INPUT (policy ACCEPT 4 packets, 200 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 4 packets, 200 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

It's default, un-configured.

With that said, I was able to get an SSH login prompt from my main machine to this secondary machine (good news the outgoing SSH rule works on my main box, eh!).

A Wireshark sreen capture:

[IMG]http://img713.imageshack.us/img713/4930/34343t.png[/IMG]

As you can see, the three way handshake occurs (with the default iptables policy on secondary machine).

Now here's the iptables output on my secondary machine with the new iptables script just processed (the interface has of course been changed because my secondary machine uses eth1 plus I have also omitted works IP address range for privacy, iptables does not really show XYZA(!)):

```

    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 0
       0        0 LOG        tcp  --  eth+   *       192.168.2.0/24       0.0.0.0/0            tcp dpt:22 LOG flags 0 level 4 prefix "** INCOMING SSH FROM LAN **"
       0        0 ACCEPT     tcp  --  eth+   *       192.168.2.0/24       0.0.0.0/0            tcp dpt:22
       0        0 LOG        tcp  --  eth+   *       X.Y.Z.A/16        0.0.0.0/0            tcp dpt:22 LOG flags 0 level 4 prefix "** INCOMING SSH FROM WORK **"
       0        0 ACCEPT     tcp  --  eth+   *       X.Y.Z.A/16        0.0.0.0/0            tcp dpt:22
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       0        0 LOG        tcp  --  *      eth+    0.0.0.0/0            192.168.2.0/24       tcp dpt:22 LOG flags 0 level 4 prefix "** OUTGOING SSH INSIDE LAN **"
       0        0 ACCEPT     tcp  --  *      eth+    0.0.0.0/0            192.168.2.0/24       tcp dpt:22
       0        0 ACCEPT     tcp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            tcp dpt:80
       0        0 ACCEPT     tcp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            tcp dpt:443
       0        0 ACCEPT     udp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            udp dpt:53
       0        0 ACCEPT     udp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            udp dpts:67:68
       0        0 ACCEPT     udp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            udp dpt:1194
       0        0 ACCEPT     udp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            udp dpt:10010
       0        0 ACCEPT     udp  --  *      eth+    0.0.0.0/0            0.0.0.0/0            udp dpt:10020
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

Before implementing the script incoming SSH worked, and after implementing the script SSH also works for incoming SSH connections on my secondary machine. This is also shown in this Wireshark capture:

[IMG]http://img715.imageshack.us/img715/7006/3434u.png[/IMG]

So I can only conclude by this then that my main machine (192.168.2.4) has the problem and it cannot be related to the new script for iptables since evidently it is working for my secondary box.

There has to be another problem. Just off top of my head, it can't be anything do with my Linksys router that's running DD-WRT firmware (and also iptables too) since the RST ACK packet comes directly from my main machine as seen in Wireshark (with the new script), plus, the router isn't blocking SYN ACK packets from my main machine as SYN ACK packets are not even seen leaving my main box on any occasion for connections initiated locally and incoming. But then again, why *would* it do that... Just a thought then.

I think I'll have to get a 11.04 VM and run it on my secondary machine, bridge the connection and do a before and after.

The Ubuntu Help Page on iptables is nagging in the back of my mind where it mentioned the issue with running NetworkManager and managing your own iptables: [https://help.ubuntu.com/community/IptablesHowTo#Configuration on startup]("https://help.ubuntu.com/community/IptablesHowTo#Configuration on startup")

Other than that I'm going to have to do some reading around on this. But what are your immediate thoughts with this update?

---

### Post by qwertyface on 2011-06-27
Definite problem here unrelated to iptables, I can confirm that.

I rebooted my main machine so as to restore the default, un-configured iptables policies/rules (I have not yet set the script to be saved and run at boot time).

Here's the terminal output:
```
#iptables -vnx -L
Chain INPUT (policy ACCEPT 1597 packets, 286865 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 119 packets, 18166 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

Now, I returned to my secondary box and tried for another SSH connection. It was refused by my main machine. Here's a screenshot:

[IMG]http://img88.imageshack.us/img88/3584/2323j.png[/IMG]

Am I missing something really simple here?

---

### Post by Doug S on 2011-06-27
It sounds to me as though sshd is not even running on the problem machine.
If it is not running then an RST packet will be returned.
I killed the sshd process on my old old unubtu server box and then tried to start a ssh session. I don't have wireshark on that computer (I guess I could have run it from this windows computer that I was running putty from, but I didn't), so I ran tcpdump instead (192.168.111.100 is my windows computer running putty; 192.168.111.140 is my old old ubuntu server NOT running sshd):
```
 
2011-06-27 11:35:12.123667 arp who-has 192.168.111.140 tell 192.168.111.100
2011-06-27 11:35:12.123861 arp reply 192.168.111.140 is-at 00:50:ba:4d:0a:3f
2011-06-27 11:35:12.125781 IP 192.168.111.100.3819 > 192.168.111.140.22: S 1395625395:1395625395(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
2011-06-27 11:35:12.126318 IP 192.168.111.140.22 > 192.168.111.100.3819: R 0:0(0) ack 1395625396 win 0
2011-06-27 11:35:12.622260 IP 192.168.111.100.3819 > 192.168.111.140.22: S 1395625395:1395625395(0) win 8192 <mss 1460,nop,wscale 2,nop,nop,sackOK>
2011-06-27 11:35:12.622661 IP 192.168.111.140.22 > 192.168.111.100.3819: R 0:0(0) ack 1 win 0
2011-06-27 11:35:13.121304 IP 192.168.111.100.3819 > 192.168.111.140.22: S 1395625395:1395625395(0) win 8192 <mss 1460,nop,nop,sackOK>
2011-06-27 11:35:13.121835 IP 192.168.111.140.22 > 192.168.111.100.3819: R 0:0(0) ack 1 win 0
2011-06-27 11:35:17.122894 arp who-has 192.168.111.100 tell 192.168.111.140
 

```
notice how it tries 3 times to create a TCP session but each time the reply is a packet with the RST and ACK bits set.
When sshd is running you should be able to observe the process via:
```
doug@test-smy:~$ ps aux | grep sshd
root      4185  0.0  0.8   4764  1048 ?        Ss   11:39   0:00 /usr/sbin/sshd
root      4189  0.0  1.9   7524  2484 ?        Ss   11:40   0:00 sshd: doug@pts/0
doug      4216  0.0  0.6   2880   812 pts/0    S+   11:52   0:00 grep sshd

```
The above shows the process and my session ( I have started the ssh daemon again and am using it to make this reply). I did:
```
 
sudo /etc/init.d/ssh start

```

---

### Post by qwertyface on 2011-06-27
> **Doug S said:**
> It sounds to me as though sshd is not even running on the problem machine.

... Man, I'm so annoyed I didn't check that. Uber n00b. All workings now. Thanks for all your help.

---

