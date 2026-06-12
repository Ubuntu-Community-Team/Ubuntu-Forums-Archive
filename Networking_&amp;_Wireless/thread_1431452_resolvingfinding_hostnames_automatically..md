---
title: "resolving/finding hostnames automatically."
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by lain on 2010-03-16
Hi all.
Sorry if this has already been asked but i've searched and searched without finding any real answer.

I have a ubuntu server running which acts as a firewall/dhcp router for sharing internet to all computers on the network. On the network i have my stationary computer (win7) and my laptop (macbook).
The server has 3 nics installed.
ETH2 for internet. ETH1 (192.168.1.2) for windows pc. ETH0 for macbook (192.168.2.2).

I can share files no problems over the network. Between windows <-> server, macbook <-> server, windows <-> macbook.
The problem i'm experiencing is that i can't seem to find either hostnames between windows and macbook. They connect to each other fine with the right ip addresses, but they can't seem to connect when using computer names.
On both the macbook and windows pc i can see the server and connect to it without using the ip adress.
What can i do to make them see each other with their computer names? Is there anything i can install on the server and configure in order for it to work automatically?
In osx you have a tab in the finder that says "shared" which shows the computers on the network and only my server pops up.
The same in windows, i can only see the server but not the macbook.
As said, it works perfectly fine if i use \\192.168.2.2 (or smb://192.168.1.2 on the macbook) but i'd rather be able to connect via the computer names.
Would also love if they could resolve automatically so when a friend connects to the network i'll see his computer name right from the start, without any re-configuration.

I'm a newbie when it comes to setting up servers, but managed to get most working by my self. Thanks in advance!

---

### Post by Iowan on 2010-03-16
I installed DNSMasq on my server. It bridges DNS and DHCP - clients get DHCP address, and can see other DHCP clients by name.

---

### Post by lain on 2010-03-16
> **Iowan said:**
> I installed DNSMasq on my server. It bridges DNS and DHCP - clients get DHCP address, and can see other DHCP clients by name.

Hm, i use dhcpd for giving out dhcp addresses over the lan and it works fine.
I installed the dnsmasq package but i dunno how to configure it in order to resolve/access other computers on the lan via computer name.

---

### Post by capscrew on 2010-03-16
> **lain said:**
> Hi all.
Sorry if this has already been asked but i've searched and searched without finding any real answer.

I have a ubuntu server running which acts as a firewall/dhcp router for sharing internet to all computers on the network. On the network i have my stationary computer (win7) and my laptop (macbook).
The server has 3 nics installed.
ETH2 for internet. ETH1 (192.168.1.2) for windows pc. ETH0 for macbook (192.168.2.2).

I can share files no problems over the network. Between windows <-> server, macbook <-> server, windows <-> macbook.
The problem i'm experiencing is that i can't seem to find either hostnames between windows and macbook. They connect to each other fine with the right ip addresses, but they can't seem to connect when using computer names.
On both the macbook and windows pc i can see the server and connect to it without using the ip adress.
What can i do to make them see each other with their computer names? Is there anything i can install on the server and configure in order for it to work automatically?
In osx you have a tab in the finder that says "shared" which shows the computers on the network and only my server pops up.
The same in windows, i can only see the server but not the macbook.
As said, it works perfectly fine if i use \\192.168.2.2 (or smb://192.168.1.2 on the macbook) but i'd rather be able to connect via the computer names.
Would also love if they could resolve automatically so when a friend connects to the network i'll see his computer name right from the start, without any re-configuration.

I'm a newbie when it comes to setting up servers, but managed to get most working by my self. Thanks in advance!

This is a tortured path for LAN communications. 

I believe you problems lie with your choice of using 3 NIC's in your server.  A more typical setup would have the three hosts (Mac, Win and Ubuntu connected to a switch (or hub) for layer 2 (Ethernet) connectivity.  Then the switch is connected to the router for Layer 3 (TCP/IP) internet access.  

The three hosts only need talk to each other over Ethernet using ARP via the switch.  How have you configured the Server (Ubuntu for LAN communications?

---

### Post by lain on 2010-03-17
> **capscrew said:**
> This is a tortured path for LAN communications. 

I believe you problems lie with your choice of using 3 NIC's in your server.  A more typical setup would have the three hosts (Mac, Win and Ubuntu connected to a switch (or hub) for layer 2 (Ethernet) connectivity.  Then the switch is connected to the router for Layer 3 (TCP/IP) internet access.  

The three hosts only need talk to each other over Ethernet using ARP via the switch.  How have you configured the Server (Ubuntu for LAN communications?

Yes, that's a more typical way. I was under the impression that using three nic's would be the same (or atleast similar to) as having a three port hub/switch.
If i understand correctly, you're saying that it's  impossible to get Win and Mac to see each others names because they're on different subnets? there's no way using two (the third gets it's ip from a remote dhcp server) installed nics on the same subnet?
The whole point of using my ubuntu server is using it as a router/switch/hub/firewall.

I don't quite understand the last question. What configuration do you need to know? I use dhcpd for dhcp sharing. bind9 is installed but haven't touched it. shorewall for simplified firewall configuration, and webmin for simpler configuration of most of the settings. What can't be done in webmin i ssh to the server.

Err, seems i mistook subnets for ip adresses.
This is how my /etc/network/interfaces look like if it can help:

```
# The loopback network interface
auto lo eth2 eth0 eth1 eth3

# The primary network interface (Internet)
iface eth3 inet dhcp

# Over
iface eth0 inet static
      address 192.168.0.1
      network 192.168.0.0
      netmask 255.255.255.0
      broadcast 192.168.0.255

#Under
iface eth1 inet static
      address 192.168.1.1
      network 192.168.1.0
      netmask 255.255.255.0
      broadcast 192.168.1.255

#Third
iface eth2 inet static
      address 192.168.2.1
      network 192.168.2.0
      netmask 255.255.255.0
      broadcast 192.168.1.255
```

And this is how my /etch/dhcp3/dhcpd.conf looks like.

```
ddns-updates on;
option subnet-mask 255.255.255.0;
# Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: http://www.isc.org/sw/dhcp/
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server.
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc;

# this may be required for some network configurations,

# assign the remote dhcp server hostname/ip addresses
option domain-name-servers 192.168.0.1, 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS
#

# assign the default lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;



##########################################################
# end config
# judas (none)
subnet 192.168.0.0 netmask 255.255.255.0 {
        option domain-name-servers 192.168.0.1;
        option broadcast-address 192.168.0.255;
        option subnet-mask 255.255.255.0;
        option routers 192.168.0.1;
        range 192.168.0.1 192.168.0.10;
        }
# navi (win)
subnet 192.168.1.0 netmask 255.255.255.0 {
        option domain-name-servers 192.168.1.1;
        option broadcast-address 192.168.1.255;
        option subnet-mask 255.255.255.0;
        option routers 192.168.1.1;
        range 192.168.1.1 192.168.1.10;
        # navi
        host navi {
                hardware ethernet xx:xx:xx:xx:xx:xx;
                fixed-address 192.168.1.2;
                }
        }
# mavi (mac)
subnet 192.168.2.0 netmask 255.255.255.0 {
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.2.1;
        option broadcast-address 192.168.2.255;
        option routers 192.168.2.1;
        range 192.168.2.1 192.168.2.10;
        # mavi
        host mavi {
                hardware ethernet xx:xx:xx:xx:xx:xx;
                fixed-address 192.168.2.2;
                }
        }

```

---

### Post by capscrew on 2010-03-17
> **lain said:**
> Yes, that's a more typical way. I was under the impression that using three nic's would be the same (or at least similar to) as having a three port hub/switch.

If i understand correctly, you're saying that it's  impossible to get Win and Mac to see each others names because they're on different subnets?


They don't see the each other via ARP or broadcast.  Plus you have no DNS resolution (BIND).  These are needed to maintain hostnames or COMPUTER names.  This is why you are also having trouble browsing the shares.   
> 

there's no way using two (the third gets it's ip from a remote dhcp server) installed nics on the same subnet?

What do you mean here?> 
The whole point of using my ubuntu server is using it as a router/switch/hub/firewall.
How have you configured the routing?> 

I don't quite understand the last question. What configuration do you need to know? 

It would be nice to understand all of what you have done.  This means: How did you connect the devices physically and logically.  I can see some of the problems now, but not all of the various settings.
> 


I use dhcpd for dhcp sharing.What do you mean by sharing?> 

 bind9 is installed but haven't touched it. BIND9 is how you map hostnames to IP addresses.  That's what started this conversation: right?> shorewall for simplified firewall configuration,


How did you configure your routing?  What are your FW settings.
> 

 and webmin for simpler configuration of most of the settings. What can't be done in webmin i ssh to the server.

Err, seems i mistook subnets for ip adresses.


If I get your drift on you physical arrangement you have an IP address via DHCP supplied to you from someone else.  The rest of the arrangement is under your control.  Is this correct?  Can you provide more detail on this "remote DHCP server"?  Who manages it?

---

### Post by lain on 2010-03-17
> **capscrew said:**
> They don't see the each other via ARP or broadcast.  Plus you have no DNS resolution (BIND).  These are needed to maintain hostnames or COMPUTER names.  This is why you are also having trouble browsing the shares.   

> What do you mean here?
Nevermind that. I was just thinking of having nic 1 share ip-range 192.168.1.2-192.168.0.10 and nic 2 share 192.168.1.11-192.168.0.20, And maybe simplify the process. But iirc that doesn't even work.

> How have you configured the routing?
I can't exactly remember since it's been a while since i configured it. I use dhcpd with three different subnets (I actually have 4 nics installed but one isn't being used atm) as seen in the config file. I then have shorewall for masquerading, and i think that's pretty much it?
This is the masq file.
```
#
# Shorewall version 4 - Masq file
#
# For information about entries in this file, type "man shorewall-masq"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-masq.html
#
###############################################################################
#INTERFACE		SOURCE		ADDRESS		PROTO	PORT(S)	IPSEC	MARK
eth3	eth0
eth3	eth1
eth3	eth2
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```


> It would be nice to understand all of what you have done.  This means: How did you connect the devices physically and logically.  I can see some of the problems now, but not all of the various settings.

Well eth3 connects to cable modem. routes traffic from there to eth0,eth1,eth2. eth1 is the windows pc. eth2 is the macbook. eth0 is not being used atm.

> What do you mean by sharing?
Well i wasn't quite clear but i was talking about the dhcpd running on my server that gives out different subnets to different nics. eth1 being my windows pc, eth2 being my macbook.

> BIND9 is how you map hostnames to IP addresses.  That's what started this conversation: right?
Hm, i guess. Seeing as what i've read every where it looks like i need to configure BIND9 in order for the hostnames to work, right? I haven't touched BIND9 at all, because i don't quite grasp it full enough to make a local dns server, that works and isn't available for the rest of the world (in lack of better words).


> How did you configure your routing?  What are your FW settings.
Hm, you got the masquerading settings. i might aswell give you the other confs.
**Zones**
```
#
# Shorewall version 4 - Zones File
#
# For information about this file, type "man shorewall-zones"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-zones.html
#
###############################################################################
#ZONE	TYPE		OPTIONS		IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4				#
loc	ipv4				#
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE

```

**Interfaces**
```
#
# Shorewall version 4 - Interfaces File
#
# For information about entries in this file, type "man shorewall-interfaces"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-interfaces.html
#
###############################################################################
#ZONE	INTERFACE	BROADCAST	OPTIONS
net	eth3	detect	norfc1918,routefilter,blacklist,tcpflags,logmartians,nosmurfs
loc	eth0	detect	blacklist
loc	eth1	detect	blacklist
loc	eth2	detect  blacklist
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

**Policies**
```
#
# Shorewall version 4 - Policy File
#
# For information about entries in this file, type "man shorewall-policy"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-policy.html
#
###############################################################################
#SOURCE	DEST	POLICY		LOG	LIMIT:		CONNLIMIT:
#				LEVEL	BURST		MASK
fw	net	ACCEPT
fw      loc     ACCEPT
loc	fw	ACCEPT
loc	net	ACCEPT
net     all     DROP info
all	all	REJECT	info
#LAST LINE -- DO NOT REMOVE
```

Then i've messed with the rules for port forwarding and stuff.
Havent touched much else. If you need more info let me know. I'd love to get this fixed.


> If I get your drift on you physical arrangement you have an IP address via DHCP supplied to you from someone else.  The rest of the arrangement is under your control.  Is this correct?  Can you provide more detail on this "remote DHCP server"?  Who manages it?

It's a home server, and i have complete access to it. I access it locally via webmin and/or ssh, depending on task. Its headless so thats why.
The "remote dhcp server" was just a fancier word for the cable modem supplied by my isp.

---

### Post by capscrew on 2010-03-17
I noticed that you have no default gateway configured for these 3 hosts.  Do you want them to have internet access?  Are you "locked in" to using the setup with the 3 NIC's?

---

### Post by lain on 2010-03-17
> **capscrew said:**
> I noticed that you have no default gateway configured for these 3 hosts.  Do you want them to have internet access?  Are you "locked in" to using the setup with the 3 NIC's?

All the computers have internet access. eth2 (where mac is plugged in) gets a default gateway (192.168.2.1) and ip (192.168.2.2).
same goes for eth1 (which connects to windows pc). it states default gateway is 192.168.1.1 and ip is 192.168.1.2

---

### Post by capscrew on 2010-03-17
> **lain said:**
> All the computers have internet access. eth2 (where mac is plugged in) gets a default gateway (192.168.2.1) and ip (192.168.2.2).
same goes for eth1 (which connects to windows pc). it states default gateway is 192.168.1.1 and ip is 192.168.1.2

I should assume then that the gateway information is somewhere other than in the [FONT="Courier New"]/etc/network/interfaces [/FONT]file then.  No GW seems to be listed.```
iface eth2 inet static
      address 192.168.2.1
      network 192.168.2.0
      netmask 255.255.255.0
      broadcast 192.168.1.255
```

How about the second question: ***Are you "locked in" to using the setup with the 3 NIC's?***.  Do you have a specific need to keep it as it is?

What is you overall goal with the network?  What influenced your decisions to configure what you have now?

---

### Post by lain on 2010-03-17
> **capscrew said:**
> I should assume then that the gateway information is somewhere other than in the [FONT="Courier New"]/etc/network/interfaces [/FONT]file then.  No GW seems to be listed.```
iface eth2 inet static
      address 192.168.2.1
      network 192.168.2.0
      netmask 255.255.255.0
      broadcast 192.168.1.255
```

How about the second question: ***Are you "locked in" to using the setup with the 3 NIC's?***.  Do you have a specific need to keep it as it is?

What is you overall goal with the network?  What influenced your decisions to configure what you have now?

Well now that you mention it, it does strikes as odd. I can't recall adding the gateway information anywhere else though.
It works anyhow. Is this vital in order to fix/help me with my problem? It seems we've derailed from the actual problem and started discussing my setup and why i have it as it is.
I could add the gateway information no problem.

Well, no. I could just plug my computers (win and mac) into my cable modem if i wanted to, if that's what you're asking. I had the spare parts and built the server to see if i could manage to set it up. It's also going to become a file server once i've added more harddrives to it.

So what i need to do is configure bind9 in order for the macbook and windows to see each other as their respective names?

---

### Post by capscrew on 2010-03-17
> **lain said:**
> Well now that you mention it, it does strikes as odd. I can't recall adding the gateway information anywhere else though.
It works anyhow. Is this vital in order to fix/help me with my problem? It seems we've derailed from the actual problem and started discussing my setup and why i have it as it is.
I could add the gateway information no problem.

Well, no. I could just plug my computers (win and mac) into my cable modem if i wanted to, if that's what you're asking. I had the spare parts and built the server to see if i could manage to set it up. It's also going to become a file server once i've added more harddrives to it.

So what i need to do is configure bind9 in order for the macbook and windows to see each other as their respective names?

Yes you could...maybe.  You have a lot of non-standard variables.  BIND9 is pretty involved, but it is very flexible.

Edit:  One last thing.  Since DHCP can provide ANY IP address from it's pool, you can't guarantee that the static mapping normally used in DNS will be valid.  Decide whether DHCP is critical to the network.  If so then you need to configure dynamic DNS mapping in BIND9 or DNSmasq.

---

### Post by lain on 2010-03-17
> **capscrew said:**
> Yes you could...maybe.  You have a lot of non-standard variables.  BIND9 is pretty involved, but it is very flexible.

Edit:  One last thing.  Since DHCP can provide ANY IP address from it's pool, you can't guarantee that the static mapping normally used in DNS will be valid.  Decide whether DHCP is critical to the network.  If so then you need to configure dynamic DNS mapping in BIND9 or DNSmasq.

Hm, which are the non-standard variables?
Yeah so i've noticed. I was thinking that maybe i didn't have to go that route seeing as it just seems tedious and a little to much for just a simple home network.

Oh ok. Would making the network static instead speed up the process with configuring bind9 or dnsmasq?
The reason i've opted for dhcp is because i wanted it to be as easy as possible for every potential user (be it friends, girlfriend, and so on) to connect. This is also somewhat the reason why i want to resolve hostnames because its easier to direct people when we want to take advantage of file sharing (instead of shouting ip adresses etc..). I'm thinking of adding a Wireless card later on so i can have users pop in and out without having to worry about how many ethernet ports i have and bother with cables.

If i still want to use DHCP, i need to setup dynamic dns mapping, correct? How does this work exactly? Will this allow newly connected computers to be automatically seen by their hostnames/netbios name/computer name?

---

### Post by capscrew on 2010-03-17
> **lain said:**
> Hm, which are the non-standard variables?
To begin with Webmin and Shorewall provide their own scripts for configuration.  They do not always follow standards to achieve their configuration.  How about the unusual topology you have chosen; That in itself is a variable. > 

Yeah so i've noticed. I was thinking that maybe i didn't have to go that route seeing as it just seems tedious and a little to much for just a simple home network.
I'm assuming you are referring to BIND9 here.  Your network is not simple.  :p It doesn't even appear to be by design.  It just happened. > 

Oh ok. Would making the network static instead speed up the process with configuring bind9 or dnsmasq?
Not really it is just one of those variables you need to consider.  Simple (to configure) or complex (accommodating more features). > 
The reason i've opted for dhcp is because i wanted it to be as easy as possible for every potential user (be it friends, girlfriend, and so on) to connect. 
You don't need to have every host on the network DHCP or static.  You can have both.  Consider having a pool of addresses for your friends to connect with and your hosts configured static.  The pool does not have to cover the whole range of IP addresses in a subnet.  I have DHCP for my laptops only.  My pool is only 10 IP addresses out of a network that has 254 legit IP addresses.  The servers, my desktop and printers are all configured static (NO DHCP).> 
This is also somewhat the reason why i want to resolve hostnames because its easier to direct people when we want to take advantage of file sharing (instead of shouting ip adresses etc..). I'm thinking of adding a Wireless card later on so i can have users pop in and out without having to worry about how many ethernet ports i have and bother with cables.

If i still want to use DHCP, i need to setup dynamic dns mapping, correct? How does this work exactly? Will this allow newly connected computers to be automatically seen by their hostnames/netbios name/computer name?

Could be done with both BIND9 and DNSmasq.  I will say that you have needlessly made you network complex in having 3 subnets when you only need 1.

---

### Post by lain on 2010-03-18
> **capscrew said:**
> To begin with Webmin and Shorewall provide their own scripts for configuration.  They do not always follow standards to achieve their configuration.  How about the unusual topology you have chosen; That in itself is a variable. I'm assuming you are referring to BIND9 here.  Your network is not simple.  :p It doesn't even appear to be by design.  It just happened. Not really it is just one of those variables you need to consider.  Simple (to configure) or complex (accommodating more features). You don't need to have every host on the network DHCP or static.  You can have both.  Consider having a pool of addresses for your friends to connect with and your hosts configured static.  The pool does not have to cover the whole range of IP addresses in a subnet.  I have DHCP for my laptops only.  My pool is only 10 IP addresses out of a network that has 254 legit IP addresses.  The servers, my desktop and printers are all configured static (NO DHCP).

Yeah it makes sense to have only some of the pool as dhcp, while having all the computers that's always connected static. I will look into it.
Care to help me simplify it then? It's just a home server.


> 
Could be done with both BIND9 and DNSmasq.  I will say that you have needlessly made you network complex in having 3 subnets when you only need 1.


Sure, but i was under the impression that when using different nics on one computer (the server) every card had to have a different subnet? IIRC i tried to configure it so it would have just one subnet but i couldn't get it to work.
Having only one subnet would make everything easier.

After seeing my confs, what do i need to do in order to get them under the same subnet?
I could put windows pc as static as 192.168.x.2, and macbook static as 192.168.x.3, while still having 192.168.x.4-10 open for dhcp?

Again, the reason i have that amount of nics in the server is because the nics only got one port each.
I've been reading some and came upon this thread:
[http://ubuntuforums.org/showthread.php?t=1405144](http://ubuntuforums.org/showthread.php?t=1405144)

In there it states that using the same subnet for different nics isn't really the right way to go.

I also added "gateway 192.168.0.1" "gateway 192.168.1.1" and "gateway 192.168.2.1" in my /etc/network/interfaces and it seems to work.

---

### Post by capscrew on 2010-03-18
> **lain said:**
> Yeah it makes sense to have only some of the pool as dhcp, while having all the computers that's always connected static. I will look into it.  Care to help me simplify it then? It's just a home server.
I have enough information to help you create a simple network, but have other projects that need my attention most of the day.  At this point I think you should leave it alone until we both agree on a plan of action.> 

Sure, but i was under the impression that when using different nics on one computer (the server) every card had to have a different subnet? 


I think at this time you should spend a little time reading up on how [**_[COLOR="Blue"]TCP/IP[/COLOR]_**]("http://www.google.com/search?hl=en&q=tcp+ip+protocol&aq=0&aqi=g10&aql=&oq=tcp+ip&gs_rfai=") model works.

You have to look at the NICS from the point of view TCP/IP.  In that case they are destination points.  If all 3 are in the same subnet then you have routing loops.  There is a routine to stop that called Spanning Tree.  This turns off all but 1 NIC to provide orderly IP traffic.

You are forced to use different subnets because that is what a router does.  It is a multi-homed device (multiple IP interfaces) to route IP traffic between different networks (subnets).

You really have to look at this (after reading the link I provided above) as a stack of differing protocols (most use the example of a layer cake).
```
Layer 1 = physical (hardware)
Layer 2a = Link (physical to the bitstream) - ARP
layer 2b = Frame (protocol)-  IP to Ethernet
Layer 3 =IP = Network IP addressing
layer 4 =TCP Transportation of network packets
```

You created a network that has no thought to Layer 2 protocols.

> 

IIRC i tried to configure it so it would have just one subnet but i couldn't get it to work.
Having only one subnet would make everything easier.
You will find it handy to write down in a journal the configurations and why you chose them.  That way you don't have to rely on your memory as to what and why you did something.> 

After seeing my confs, what do i need to do in order to get them under the same subnet?
I could put windows pc as static as 192.168.x.2, and macbook static as 192.168.x.3, while still having 192.168.x.4-10 open for dhcp?

I will be back later in the day.  Right now just read up on IP networking.

Again, the reason i have that amount of nics in the server is because the nics only got one port each.
I've been reading some and came upon this thread:
[http://ubuntuforums.org/showthread.php?t=1405144](http://ubuntuforums.org/showthread.php?t=1405144)

In there it states that using the same subnet for different nics isn't really the right way to go.


Like I said it is a misapplication of technology to have 3 NIC's for one subnet.  What you need is 2 NIC's in the router (server).  One NIC talks to the cable modem and the other NIC talks to you network.  You need a switch to provide the multiple Ethernet (layer 2) connections.  See the above chart.  A switch provides the multiple ports that allows you to connect all of your devices to the one NIC in the server.

Then we can simplify what we need for IP addressing/DHCP/DNS and FW setup.

---

### Post by lain on 2010-03-18
> **capscrew said:**
> I have enough information to help you create a simple network, but have other projects that need my attention most of the day.  At this point I think you should leave it alone until we both agree on a plan of action.
I think at this time you should spend a little time reading up on how [**_[COLOR="Blue"]TCP/IP[/COLOR]_**]("http://www.google.com/search?hl=en&q=tcp+ip+protocol&aq=0&aqi=g10&aql=&oq=tcp+ip&gs_rfai=") model works.

Was it suppose to redirect to google? cause i know how to google :P
Well i'm going away for a few weeks on saturday and won't have access to my server then. I was thinking of getting this done before i left but it looks like i have to get a switch in order to set it up, which i can't until the end of next month.

> You have to look at the NICS from the point of view TCP/IP.  In that case they are destination points.  If all 3 are in the same subnet then you have routing loops.  There is a routine to stop that called Spanning Tree.  This turns off all but 1 NIC to provide orderly IP traffic.

Yes, that was what i had read as well.
This is not wanted with my current setup.

> 
You are forced to use different subnets because that is what a router does.  It is a multi-homed device (multiple IP interfaces) to route IP traffic between different networks (subnets).

Ok i understand.

> You really have to look at this (after reading the link I provided above) as a stack of differing protocols (most use the example of a layer cake).
```
Layer 1 = physical (hardware)
Layer 2a = Link (physical to the bitstream) - ARP
layer 2b = Frame (protocol)-  IP to Ethernet
Layer 3 =IP = Network IP addressing
layer 4 =TCP Transportation of network packets
```

You created a network that has no thought to Layer 2 protocols.

I understand that now. I don't quite grasp networking on a more advanced level, besides the basic. This is the reason why my setup looks like it does.

> You will find it handy to write down in a journal the configurations and why you chose them.  That way you don't have to rely on your memory as to what and why you did something.

Yeah i know :P
When i was setting it up i was just eager to get internet working on both of the other computers and never paid attention to writing down different configs.

> 
Like I said it is a misapplication of technology to have 3 NIC's for one subnet.  What you need is 2 NIC's in the router (server).  One NIC talks to the cable modem and the other NIC talks to you network.  You need a switch to provide the multiple Ethernet (layer 2) connections.  See the above chart.  A switch provides the multiple ports that allows you to connect all of your devices to the one NIC in the server.

Then we can simplify what we need for IP addressing/DHCP/DNS and FW setup.

Yeah as i said, i thought that having different nics would work just like a switch/hub/router, but now i know thats not the case.
Its been awhile since i dealt with a switch, but wouldn't that automatically give out ip adresses without the need of a server?
Excuse me if i'm mistaken. What would be the point of using the server then?

[EDIT 1]
Oh i forgot to say thank you for taking the time to educate me, and that you're willing to help me setup a better network.

[EDIT 2]
Another question. If i wanted to bring in Wlan into the picture after purchasing and setting up the switch, what would be the easiest way?
Say that we do this kind of config:

MODEM (internet) <- Server NIC1. Server NIC2 <- SWITCH (with x ports) <-  x computers.

When i've got all the parts (which will take some months), I'm going to have WIN PC connected via LAN. A HTPC connected via LAN. Macbook connected via WLAN (so i can move it around).
I was thinking of having the server also act as a file server (as stated before) and let the HTPC stream media contents from it. 
I want the server to act as a firewall and a seedbox as well.
The HTPC is a future project and i don't have any parts to build it yet, but i wanted to give you the full picture in order to understand what i'm trying to accomplish.
People who visits should also be able to connect via lan or wlan, preferably via dhcp, but it isn't vital. Would be a lot less hassle but most of my friends know how to configure static ip.
All my home computers (win pc, macbook, htpc) can be static. Would love to setup a network printer as well, but it's not prioritised atm.
The wlan dhcp pool would only be like 10. Same goes for lan (depending on how many ports my switch will have i guess).

---

### Post by Iowan on 2010-03-18
> **lain said:**
> 
Its been awhile since i dealt with a switch, but wouldn't that automatically give out ip adresses without the need of a server?
Excuse me if i'm mistaken. What would be the point of using the server then?
The switches with which I'm familiar (unmanaged), do not give out IP addresses. They learn which addresses are on which ports - so traffic can be directed down only one port - instead of broadcasting on all ports (like a hub).

---

### Post by capscrew on 2010-03-18
> **lain said:**
> Was it suppose to redirect to google? cause i know how to google :P
Well i'm going away for a few weeks on saturday and won't have access to my server then. I was thinking of getting this done before i left but it looks like i have to get a switch in order to set it up, which i can't until the end of next month.

I will be here when you need me.  You do not have to spend a lot of money on a switch.  I have a simple D-Link un-managed 8 port switch.> 
...

Its been awhile since i dealt with a switch, but wouldn't that automatically give out ip adresses without the need of a server?
Excuse me if i'm mistaken. What would be the point of using the server then?


Now that that we have that spiffy chart of the  networking layers I can cut to the chase.  A switch works on **layer 2**.  The communication is via ARP (the media access control number (MAC)).  There is no need for an IP address with a layer 2 switch.

The host that you call *"the server"* is still needed to provide the routing and firewall services along with DHCP.  If we install DNSmasq or run BIND9, it will be on this host.

To me a server is a process running on a host waiting to respond to a client request.  So your router/DHCP/DNS servers run on that host.
  
> 

[EDIT 1]
Oh i forgot to say thank you for taking the time to educate me, and that you're willing to help me setup a better network.

You're welcome.> 

[EDIT 2]
Another question. If i wanted to bring in Wlan into the picture after purchasing and setting up the switch, what would be the easiest way?
Say that we do this kind of config:

MODEM (internet) <- Server NIC1. Server NIC2 <- SWITCH (with x ports) <-  x computers.

Easy.  We plug a wireless access point (WAP) into one of the free ports on the switch.  

WLan connections are in 2 parts. The RF to provide the bitstream connection (kinda like the physical layer) and the 802.11 b/g/n layer 2.  The TCP/IP runs on top of that.  As you can see having the various layers allows flexibility.
> 

When i've got all the parts (which will take some months), I'm going to have WIN PC connected via LAN. A HTPC connected via LAN. Macbook connected via WLAN (so i can move it around).

This is how I have it.  > 
I was thinking of having the server also act as a file server (as stated before) and let the HTPC stream media contents from it.
That will work perfectly.> 
 
I want the server to act as a firewall and a seedbox as well.

When it is setup as you described you can think of the Router/FW/DNS?DHCP host (the server) as an *"edge device"*.  It provides the services that are coming into and out of your network (at the edge).  The other services (file services/ printer) can run there too.
> 

The HTPC is a future project and i don't have any parts to build it yet, but i wanted to give you the full picture in order to understand what i'm trying to accomplish.
Thinking ahead.  Very important in network design.> 

People who visits should also be able to connect via lan or wlan, preferably via dhcp, but it isn't vital. 
Very easy once we have the basic network sorted out.> 

Would be a lot less hassle but most of my friends know how to configure static ip.
All my home computers (win pc, macbook, htpc) can be static. Would love to setup a network printer as well, but it's not prioritised atm.
The wlan dhcp pool would only be like 10. Same goes for lan (depending on how many ports my switch will have i guess).
Actually the entire range of available addresses is set by the subnet mask.  That thing that looks like this:255.255.255.0.  :D

The pool of DHCP addresses is configured out of the entire range.  The amout of ports only limits how many physical devices can be connected.

You can plug a switch to another switch to increase your amount of connections.  But (as we have found out), you can't loop 2 hosts on the 2 switches (remember spanning tree?).

---

### Post by capscrew on 2010-03-18
> **Iowan said:**
> The switches with which I'm familiar (unmanaged), do not give out IP addresses. They learn which addresses are on which ports - so traffic can be directed down only one port - instead of broadcasting on all ports (like a hub).

Hi Iowan,

I love being a stickler for detail and I get to teach.  The addresses are the MAC address.  ARP is what looks for and caches them.  If it is a switch the chip (silicon) remembers what MAC address is on what port. 

With a hub the ports are common to all.  ALL layer 2 traffic are on the same bus and can (and does) collide.  This for sure slows down traffic.  There are specific methods to determine how the collisions are resolved.  I haven't had a hub in any of my networks in 10 years for just that reason.

---

### Post by lain on 2010-03-19
> **capscrew said:**
> Hi Iowan,

I love being a stickler for detail and I get to teach.  The addresses are the MAC address.  ARP is what looks for and caches them.  If it is a switch the chip (silicon) remembers what MAC address is on what port. 

With a hub the ports are common to all.  ALL layer 2 traffic are on the same bus and can (and does) collide.  This for sure slows down traffic.  There are specific methods to determine how the collisions are resolved.  I haven't had a hub in any of my networks in 10 years for just that reason.

I'm going to answer to the longer post later because i'm a little stressed but i wanted to ask while i still remember.
ARP caches and stores MAC address, right? How long does it store this information? Does it get flushed out once the host disconnects from the switch port? This is merely a question from an eductional standpoint.

Oh so that's why hubs where never recommended then? We always looked for someone with a switch when we had our lan parties back in the day, because "using a hub is going to be slow and unbearable when transfering/sharing files". When we couldn't get a hold of a switch we always had to come up with a plan when to transfer files (usually when everyone went to bed). Good times.

---

### Post by capscrew on 2010-03-19
> **lain said:**
> I'm going to answer to the longer post later because i'm a little stressed but i wanted to ask while i still remember.

ARP caches and stores MAC address, right? How long does it store this information? Does it get flushed out once the host disconnects from the switch port? This is merely a question from an eductional standpoint.

The MAC address is what is stored (cached).  ARP is what requests it.  The cache is a configurable parameter.  Your server (router might have between 2 and 15 minutes of TTL (time to live) for it's cache.  A router buried somewhere in an enterprise environment (with mostly static routes) might have days worth of TTL configured in.

Check out [**_[COLOR="Blue"]this link[/COLOR]_**]("http://www.petri.co.il/csc_arp_cache.htm") for a good description of ARP and IP networking. > 

Oh so that's why hubs where never recommended then?
Yes, because of the crowded *collision domain*.
Everyone talking at the same time on the same wire. > 

We always looked for someone with a switch when we had our lan parties back in the day, because "using a hub is going to be slow and unbearable when transfering/sharing files". When we couldn't get a hold of a switch we always had to come up with a plan when to transfer files (usually when everyone went to bed). Good times.
When switches first became available I was working for a large university.  We had a main switch for each floor of each building.  Then we had multiple switches for the classroom.  

We eliminated a lot of copper cabling.  We were also in the process of converting from CAT5 to CAT6 while upgrading to 100Mbs NIC's.

---

