---
title: "how to setup static ips on two network adapters"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by iishiii on 2010-01-21
Hello Everyone 

i am very new to Linux and installed ubuntu 9.10  and squid for cache purpose.
i have pluged [COLOR=Red]2 Eather Net Cards [/COLOR]one for internal and one for External 

My ISP ip setting are 

 [COLOR=Red]Address                192.168.1.2
 Subnet Mask         255.255.255.0
Default Gateway     192.168.1.1

Preferred DNS server 208.67.2220.220
Alternative DNS Server 208.67.222.222[/COLOR]

i want to configure these setting for my eth0  ( for in coming net from Modem )


And also want to Give IP to LAN ( eth1 ) which will be connected to switch for other users to access cache 

Help me i will be very thank ful to you peoples

---

### Post by iishiii on 2010-01-21
Hello Everyone 

i am very new to Linux and installed ubuntu 9.10  and squid for cache purpose.
i have pluged [COLOR=Red]2 Eather Net Cards [/COLOR]one for internal and one for External 

My ISP ip setting are 

 [COLOR=Red]Address                192.168.1.2
 Subnet Mask         255.255.255.0
Default Gateway     192.168.1.1

Preferred DNS server 208.67.2220.220
Alternative DNS Server 208.67.222.222[/COLOR]

i want to configure these setting for my eth0  ( for in coming net from Modem )


And also want to Give IP to LAN ( eth1 ) which will be connected to switch for other users to access cache 

kindly guide me step by step please

Help me i will be very thank ful to you peoples

---

### Post by iishiii on 2010-01-21
**how to setup static ips on two network adapters** 			
 			 			 		   		 		 		Hello Everyone 

i am very new to Linux and installed ubuntu 9.10  and squid for cache purpose.
i have pluged [COLOR=Red]2 Eather Net Cards [/COLOR]one for internal and one for External 

My ISP ip setting are 

 [COLOR=Red]Address                192.168.1.2
 Subnet Mask         255.255.255.0
Default Gateway     192.168.1.1

Preferred DNS server 208.67.2220.220
Alternative DNS Server 208.67.222.222[/COLOR]

i want to configure these setting for my eth0  ( for in coming net from Modem )


And also want to Give IP to LAN ( eth1 ) which will be connected to switch for other users to access cache 

kindly guide me step by step please

Help me i will be very thank ful to you peoples

---

### Post by iishiii on 2010-01-21
**how to setup static ips on two network adapters** 			
 			 			 		   		 		 		Hello Everyone 

i am very new to Linux and installed ubuntu 9.10  and squid for cache purpose.
i have pluged [COLOR=Red]2 Eather Net Cards [/COLOR]one for internal and one for External 

My ISP ip setting are 

 [COLOR=Red]Address                192.168.1.2
 Subnet Mask         255.255.255.0
Default Gateway     192.168.1.1

Preferred DNS server 208.67.2220.220
Alternative DNS Server 208.67.222.222[/COLOR]

i want to configure these setting for my eth0  ( for in coming net from Modem )


And also want to Give IP to LAN ( eth1 ) which will be connected to switch for other users to access cache 

kindly guide me step by step please

Help me i will be very thank ful to you peoples

---

### Post by pirateghost on 2010-01-21
unless you are doing firewalling or routing, you can use just one NIC.  otherwise you will have to deal with bridging the nics together to make all traffic flow through

my suggestion is just to set up one nic, and set up all the clients to point to that IP for proxy

another option would be to replace your router with a linux/opensource router/firewall and utilize the transparent proxy available on nearly all of them:
vyatta < personal favorite firewall/router distro
pfsense < very nice freebsd based system for firewall/router
smoothwall < i am not very fond of this one any more
endian < nice all around package
if you have decent hardware... Untangle cant be beat for ease of use. (untangle doesnt have squid but will report on usage and protect your entire network very well)

---

### Post by iishiii on 2010-01-21
i have Mikrotik OS router 
detailed diagrams is attached 

kindly guide me what should i do as best for me 
want to configure ips for this

---

### Post by pirateghost on 2010-01-21
personally, i would just hang it off the switch, and make all the clients browsers point to it for proxy

from your diagram you want to put it UPSTREAM from your router and would still require some bridging of the nics, which is probably a very bad idea....

keep the set up simple.  set an ip address up for the ubuntu box, stick it on the switch somewhere, and point the clients to it.  i have a similar setup, but am using vyatta as my squid box.  only need one IP address, and one nic

---

### Post by iponeverything on 2010-01-21
Just add the relevant lines to /etc/network/interfaces

if you do a "man interfaces" the man page for this is better than most..

---

### Post by iponeverything on 2010-01-21
> unless you are doing firewalling or routing, you can use just one NIC. otherwise you will have to deal with bridging the nics together to make all traffic flow through

this is not the case.

All that is necessary is turning on IP forwarding and having the correct routes on the box. If the IP range is the same on both sides of squid box, he will also have to turn on proxyarp.

---

### Post by iponeverything on 2010-01-21
iishiii -- don't crosspost.

[http://ubuntuforums.org/showthread.php?t=1386725](http://ubuntuforums.org/showthread.php?t=1386725)

---

### Post by dineshs on 2010-01-21
configuring eth is explained in
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

### Post by iishiii on 2010-01-21
cant you tell me that what should i do ..... .

Unbuntu box is only to listen all request from mikrotik router ( acting as cache ) 

want to simply one for ineternal and one for external ip setting 

kindly explain a lil bit how to do that please

---

### Post by dineshs on 2010-01-21
configuring eth0 can be done as follows
In a terminal type
```
sudo gedit /etc/network/interfaces
```
copy and paste this (The file should contain only this)

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Save the file then
```
sudo gedit /etc/resolv.conf
``` 
copy and paste this 

nameserver 208.67.222.220
nameserver 208.67.222.222

Regarding sharing I dont know exactly.What I do is running a script each time the system restarts

---

### Post by dcstar on 2010-01-21
> **iishiii said:**
> cant you tell me that what should i do ..... .

Unbuntu box is only to listen all request from mikrotik router ( acting as cache ) 

want to simply one for ineternal and one for external ip setting 

kindly explain a lil bit how to do that please

Do a forum search for connection sharing, there are existing detailed HOWTOs for **you** to find.

---

### Post by iishiii on 2010-01-21
And please tell me what should i have to do with eth1 

as per you said it will set ip for eth0 

basically i want to configure transparent squid 
[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

here 

he said 

i) Eth0: IP:192.168.1.1
iii) Eth1: IP: 192.168.2.1 (192.168.2.0/24 network (around 150 windows XP systems))
iv) OS: Red Hat Enterprise Linux 4.0 (Following instruction should work with Debian and all other Linux distros) Eth0 connected to internet and eth1 connected to local lan i.e. system act as router.

should i add lines as above you said for eth1 too ?
or not ... really confusiong with that

---

### Post by flabdablet on 2010-01-21
There are a number of things you're going to need to understand and do before this thing will fly.

First and most basic thing: IP addresses belong to a box's interfaces, not to the box itself.

Second basic thing: all the interfaces connected to a given switch should share the same IP subnet address, and each should have a distinct host address.

Third basic thing: your two-interfaces Linux box is going to need to act as a router, to ship Internet-destined packets from your other boxes off to your modem, and to ship reply packets from your modem to your other boxes.

Fourth basic thing: once your modem is connected to your Linux box's eth0, and the rest of your LAN boxes are connected to a switch attached to its eth1, then your modem is no longer going to be on the same subnet as the rest of your LAN boxes, and will not automatically know how to get packets to them. You'll have to tell it.

So, before you even think about getting Squid going, there are a number of things you need to do, just to make the network go.

First thing is to give eth0 and eth1 their own IP addresses. Each of these addresses should be on a different subnet. It's conventional to use subnets in the 192.168.x range for home LANs. It looks like your modem's DHCP server is configured to hand out addresses in the 192.168.1 subnet at present, so let's stick with that for eth0. For eth1, we'll use addresses in the 192.168.2 subnet.

So your /etc/network/interfaces will need to look like this (assuming that eth0 and eth1 are the only real interfaces installed):
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1 #your modem's own IP address

auto eth1
iface eth1 inet static
    address 192.168.2.1
    netmask 255.255.255.0
    broadcast 192.168.2.255
    up route add -host 255.255.255.255 dev eth1
    down route del -host 255.255.255.255 dev eth1

```
Note in particular that eth1 doesn't get a gateway address. This is because of what gateway addresses do: any interface that has a gateway address causes a **default route** pointing to that address to be created when it comes up, and deleted when it goes down.

A default route tells a box what to do with packets that it can't route anywhere else based on the IP addresses of its own interfaces. For example, if you asked your box to send a packet to 208.67.222.220, it would know that this IP address doesn't match the subnets of any of its own interfaces, and would therefore hand it off to 192.168.1.1 (your modem) via the interface that's on that same subnet (eth0).

As well as not having a gateway, eth1 gets a couple of extra commands added for when it's brought up and taken down. The effect of these is to associate the host address 255.255.255.255 (global broadcast) with eth1. You'll need this in order to make Windows boxes accept information from the DHCP server you're going to need to set up. Don't worry about it for now.

Once you've made your /etc/network/interfaces look like the above, and wired eth0 to your modem and eth1 to one or more of your other boxes, test it as follows:```
ping 192.168.1.1
``` should get you responses from your modem, and ```
ping 208.67.222.220
``` should get you responses from your primary DNS server.

Next thing is to set up your other box's network interface, because that interface will no longer be able to get its configuration automatically from your modem. I'm going to assume that this is a Windows box, since you said you weren't very familiar with Linux.

Automatic configuration is done using DHCP, and DHCP relies on network broadcasts, and network broadcasts are not routable between subnets; so the DHCP server built into your modem is not going to be able to reach your Windows box and vice versa. We'll fix this later on by adding a DHCP server to the Linux box, but for the time being, just use static configuration on the Windows box: tell its Local Area Connection's TCP/IP Properties to use the fixed address 192.168.2.2, mask 255.255.255.0, gateway 192.168.2.1, and DNS servers 208.67.222.220 and 208.67.222.222. Once that's done, your Linux box should be able to get ping responses from 192.168.2.2 (the Windows box).

Now, from the Windows box, you should get ping responses from 192.168.2.1 (the Linux box's eth1 interface). If you try to ping 192.168.1.2 (Linux eth0) or 192.168.1.1 (your modem) you'll get no response.

There are two blockages in the way. First, the Linux box isn't yet set up to forward packets between interfaces. Let's fix that first:```

echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
``` will turn forwarding on right now, and removing the # from the "#net.ipv4.ip_forward=1" line in /etc/sysctl.conf will make sure it gets turned on automatically on next system start.

With that in place, you should be able to ping 192.168.1.2 (Linux eth0) from your Windows box, even though that box is physically connected to the other subnet. But you still won't get responses from 192.168.1.1 (your modem).

In fact the ping requests from the Windows box should actually be making it to the modem at this stage, but your modem is not going to know where to send its responses! As far as the modem is concerned, its own LAN interface is on the 192.168.1 subnet, and the 192.168.2 subnet is therefore not LAN-accessible. So it will either send the ping response packet off into the cloud via its WAN interface, where it will be dropped by the first real router it encounters (because 192.168.x subnets are reserved for private use, and are not internet-routable) or it will drop it itself for the same reason.

To get around this, you need to set up a **static route** in your modem. Most modems will have a configuration page that lets you do this. You need to tell your modem to route packets destined for 192.168.2.x via the gateway at 192.168.1.2 - your Linux box's eth0 interface, which **is** on the modem's LAN subnet. Having done that, you should be able, from your Windows box, to get ping responses from 192.168.2.1 (Linux eth1), 192.168.1.2 (Linux eth0), 192.168.1.1 (modem), 208.67.222.220 (primary DNS server) and [www.google.com](www.google.com) (because DNS should also be working properly now on Windows).

Back to the Linux box: pinging [www.google.com](www.google.com) may work or may fail. Linux looks in /etc/resolv.conf for name servers, and if there are none there because resolv.conf is empty or missing, DNS lookups will fail. You may find /etc/resolv.conf already filled in, if eth0 has ever been plugged into your modem while set up as a DHCP-managed interface. If not, make it look like this:```

nameserver 208.67.222.220
nameserver 208.67.222.222
```
I have to go now, and we haven't set up the DHCP server on your Linux box yet. [Here's]("http://tldp.org/HOWTO/DHCP/x369.html") a guide to setting one up, after you've installed it with```
sudo apt-get install dhcp3-server
```If trying to follow that makes you go backwards, post back here; if I'm not around, I'm sure somebody else will help.

---

### Post by frodon on 2010-01-21
Duplicate thread closed.

Merged thread here:
[http://ubuntuforums.org/showthread.php?t=1386725](http://ubuntuforums.org/showthread.php?t=1386725)

---

### Post by frodon on 2010-01-21
Duplicate thread closed.

Merged thread here:
[http://ubuntuforums.org/showthread.php?t=1386725](http://ubuntuforums.org/showthread.php?t=1386725)

---

### Post by iishiii on 2010-01-21
@ flabdablet

its my pleasure to say you thank you very very much ...........

as far as you have written  i configured it... but i would not able to set static ip in modem page so that i can ping my Modem IP [192.168.1.1] 

and next i want to Configure squid transparent proxy ....... 

i will be very thankful to you again if you help as you did first.........

---

### Post by iponeverything on 2010-01-21
@flabdablet
You are much more patient than I. It became apparent very quickly that iishiii did not have the requisite foundation for someone to help him in a concise manner. Your post looks like a good outline for a book on IP routing fundamentals ;)

@iishiii
Your starting on first landing when you should be starting a bit lower. I would suggest that you first put the squid machine in place and have it do nothing except forward packets and start adding pieces from there. Attempting drop the whole thing in without the understanding required to intuit the solutions to problems, is just going to lead to a lot of frustration for you and the users on your network.

---

### Post by puttingau on 2010-01-22
I have had internet connection sharing shared with static clients in Hardy quite easily, but on changing to Karmic have spent a couple of days on it---supposed to be easy.
For me, it was only easy when I discovered
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Internet_connection_sharing_.28DHCP_server.29)
Thanks to a poster in this thread.

In [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
I note the item headed "Ubuntu 9.10 Method" didn't work for me, because it is not detailed enough, and doesn't touch on static connections.
I have also noted and been misled by posts here and there than say Firestarter is deprecated and ufw is the only way to go

edit found it necessary to add a "policy" in firestarter, to allow service DNS to port 53 for lan

---

### Post by flabdablet on 2010-01-22
*but i would not able to set static ip in modem page so that i can ping my Modem IP [192.168.1.1]*

What you want to set is not a static IP, but a static **route**. You need to tell your modem that when it wants to send a packet to any 192.168.**2**.x address, it should hand that packet to the gateway at 192.168.1.2 (your Linux box's eth0 interface).

Failure to set this up will not only mean that you can't get a ping response from your modem when you ping 192.168.1.1 from a Windows box - it will mean that none of your Windows boxes will get any response at all from any packet they send **via** the modem; that is, your Windows boxes won't be able to see the Internet.

This is a showstopper. There are ways around it (there's *always* a way around it) but these will either involve setting up network address translation inside the Linux box, or bridging your two ethernet adapters onto the same IP subnet, both of which make your life much harder later on.

So if your present modem can't set up static routes (check its manual carefully - most can) you should replace it with one that can.

---

