---
title: "Slow name resolution after accidentally running pppoe config"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by Roochiedoor on 2013-02-26
Hi,
the problem I have at the moment is since messing up my network configs etc.. the name resolution is really slow. you'll have to read below to see how I got into this state. 

I'm running a dual boot system with Xubuntu 12.04 and Win XP. I live on campus at a University in New Zealand where the Local Network is part of the university and from what I can work out, the whole university has a contract with a local ISP to manage everything that goes out their gateway. This means we are free to roam the local network but when we want to hit the net we need to have a DSL account set up with that ISP.

One of the issues I've had since using this setup is, that I'd been unable to access some Local LAN machines when I was connected to the ISP at the same time. Obviously the ISP's gateway or name lookup machine has no knowledge of the Local Network except where the University has specific servers.

When I boot into XP the machine seems to be able to work it out with out any issue. I figured it was probably a matter of getting the correct routing tables put in on my DSL connection.

(I should note that here that all my client IP's are dynamic, not my choice)

And this is where the trouble starts....
Not being much of a routing or network guru, I located a bash script that someone made at one stage for such a purpose (this was a bad move) here it is (the local ISP is called SNAP):

```
#!/bin/bash

echo -ne  "***Setting up Snap connection \n";

# Check we are disconnected from Snap
/etc/rc.d/adsl stop

#Kill dhc
killall dhcpcd
# Get dhcp address
dhcpcd eth0

# Get and store Local IP in variable $lip
lip=`ifconfig eth0 | grep "inet addr" | awk -F ":" {'print $2'} | awk {'print $1'}`

# Get and store Gateway IP in variable #gip
gip=`ip route | grep "default via" | awk {'print $3'}`

# Check that pppoeconf has been setup, if it hasn't then run it
# Not functional
#echo -ne  "Checking for dsl-provider \n";
#file="/etc/ppp/peers/dsl-provider"
#if [ -f $file ]
#then
#	echo -ne "PPPOE is already configure \n";
#else
#	`/usr/sbin/pppoeconf`
#fi

# Connect to Snap (hopefully pppoeconf has been configured)
/etc/rc.d/adsl start
# Sleep for half a second to let ppp0 come up
sleep 0.5

# Get and store WAN IP into variable $wip
wip=`ifconfig ppp0 | grep "inet addr" | awk -F ":" {'print $2'} | awk {'print $1'}`

# Set up routing
ip addr del $lip dev eth0
ip addr add ${lip}/32 dev eth0 

ip route add ${gip}/32 dev eth0
ip route add 10.8.0.0/16 via $gip dev eth0 src $lip
ip route add default via $wip
```

Not realising it was going to run pppoeconf (and not knowing that you don't run pppoeconf if running network manager - I do now), I worked through the pppoeconf wizard, and on next reboot I had network issues all over the place and no network manager to fix them with.

After a bit or Web searching, I've managed to get all of the my connections back and I'm using Network Manager again (incidentally one of the errors I kept receiving with pppoeconf when trying to pon dsl-provider was because it didn't understand the replacedefaultroute command, seems as though that should have worked). Some of the things I did was :

set /etc/NetWorkManager.conf
```
 ifupdown
managed=true 
```

remove the file /etc/network/interfaces
and upon finding nothing worked, replaced it with a file of the same name that simply contained
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I can't quite remember what else I did, but they were the main things that got me back into action with Network Manager (did a few things to get the OS to recognise the wlan0 interface again as well)

So now my PC will use my local University connection and will connect to my ISP (snap) again. Which is great, but the internet access on it is really slow to find a page. It's fine once I've got a page open (and if it's just browing a photo gallery once the page is open it's quick).

I figure there is something wrong with the name resolution

my /etc/ppp/resolv.conf simply has the following 2 entries in it
```

nameserver 202.37.101.1
nameserver 202.37.101.2

```
which I assume came from my isp

I tried turned IPV6 off as well with out any change.

It should be noted, that everything was fine before I ran the script, so the changes that make it slow would only have come from running pppoeconf.

I do have a working Windows OS image to compare my results against from the same PC and ethernet card.

In windows I have the following
```

ipconfig

ethernet adapter Local Area Connection:

Connection-specific DNS Suffix . : resnet.canterbury.ac.nz
Ip Address.......................: 10.8.26.### (keeping that private)
Subnet Mask......................: 255.255.248.0
Default Gateway..................: 10.8.31.254

PPP Adapter SNAP VPN:
Connection-specific DNS Suffix ..: <nothing>
IP Address.......................: 111.69.255.### (private)
Subnet Mask......................: 255.255.255.255
Default Gateway..................: 111.69.255.### (private same as IP)

```

In the problem Linux image if I do ifconfig I get the following: (note I hashed or ?? out the end of the IP addresses in ppp0 for privacy)
```

neilh@BackFromTheDead:/etc/ppp$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:ac:32:72  
          inet6 addr: fe80::240:d0ff:feac:3272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147571203 (147.5 MB)  TX bytes:19973619 (19.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:744111 (744.1 KB)  TX bytes:744111 (744.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:111.69.226.###  P-t-P:111.69.17.??  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:203025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:119311031 (119.3 MB)  TX bytes:15438635 (15.4 MB)

```

if I do a nslookup in windows xp [www.google.com](www.google.com) command I get
```

*** Can't find server name for address 203.0.178.191: time out
Server:   bender.snap.net.nz
Address: 202.37.101.1

(then it has the answer 1 or 2 authority answers from google)

```

In contrast my Linux OS has the following response (a lot more responses than 1 or 2 from google):
```

neilh@BackFromTheDead:/etc/ppp$ nslookup google.com
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.237.135
Name:	google.com
Address: 74.125.237.136
Name:	google.com
Address: 74.125.237.137
Name:	google.com
Address: 74.125.237.142
Name:	google.com
Address: 74.125.237.128
Name:	google.com
Address: 74.125.237.129
Name:	google.com
Address: 74.125.237.130
Name:	google.com
Address: 74.125.237.131
Name:	google.com
Address: 74.125.237.132
Name:	google.com
Address: 74.125.237.133
Name:	google.com
Address: 74.125.237.134

neilh@BackFromTheDead:/etc/ppp$

```

I can also post my Ip route tables for what the windows OS gets, the linux output is the following
* in the below code I've entered ? and # to protect my IPs (at least I think at least one of them is my IP)

```

ip route list
default via 111.69.17.22 dev ppp0  proto static 
111.69.17.## dev ppp0  proto kernel  scope link  src 111.69.226.??? 
169.254.0.0/16 dev ppp0  scope link  metric 1000 

```

I also read something about nameserver lookup being local on 12.04 and some people change this? What would you recommend (as I said before I had no issue till the script was run)

The other thing I've noticed is if I type ip addr, I'm missing two interfaces???
```

neilh@BackFromTheDead:/etc/ppp$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:40:d0:ac:32:72 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::240:d0ff:feac:3272/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:19:d2:69:e5:35 brd ff:ff:ff:ff:ff:ff
6: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 111.69.226.??? peer 111.69.17.##/32 scope global ppp0

```

What's happened to interface 4 and 5?

What do I need help with?
- Firstly I need help with getting the name resolution working at a decent pace again, I'm just not sure what part is the issue, is it the values in the resolv.conf or something else? These auto poplulated upon reconnecting to the ISP by the way

- Secondly
I'd like to figure out how to do the routing table, in retrospect I probably just needed to do that in network manager under the Routes for the DSL, but being dhcp I probably need to do it for a subnet and that's where my network knowledge runs out.

Lastly I should mention I also have L2TP IPSec VPN Manager installed, I use this to connect to my workplace through an IPsec L2TP tunnel. Usually I need to have the DSL connection running first then I fire this up (it's using xl2tp or something like that, in the back ground - still seems to work now), not sure if it's taken over anything during this process.

Any ideas anyone? What other information do you need?
I've attached windows screen shots of some of the info I get out XP for the same connection setups.

---

### Post by Roochiedoor on 2013-02-27
I believe I may have sorted out my own issue (although I can't explain why the cause had the affect it did).

I pretty much referenced this post [HTML]http://ubuntuforums.org/showthread.php?t=1195169[/HTML]

The problem was when I recreated my /etc/network/interfaces file I entered the following because this is what I had seen on everything I had googled (must have been pre Network Manager or something)
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I did not need the 3rd and 4th line. Incidentally the 3rd and 4th line were causing Network Manager to contain a default wired network called ifupdown which I couldn't remove. 
So I did the following
- Fixed the file and only keeping the first 2 lines 
- Deleted all of my setup network connections

sudo iptables -F
(basically flush out the routing tables

Rebooted
-Recreated my network connections in Network Manager, and now it all runs at normal speed

I think the combination of entering
```

auto eth0
iface eth0 inet dhcp

```
in /etc/network/interfaces

in combination with /etc/NetworkManager/NetworkManager.conf containing the values
```

[ifupdown]
managed=true

```
was conflicting somehow.
I should mention that after trying to fix the issues caused by running pppoeconfig that at some stage I had to change the value of managed=false back to managed=true

I think I was about 6 hours away from backing everything up and either trying the upgrade to 12.10 in an attempt resolve the issue or reinstalling, before I figured this out.

---

