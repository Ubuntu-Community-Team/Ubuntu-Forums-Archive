---
title: "Setting up Nat on Ubuntu 11.04"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by Christloves on 2011-05-07
I am a newbie.  I have built a server, installed Ubuntu 11.04 on it.  I have two Nic cards.

I am attached to the DSL modem thru the first card and am accessing the web on the server.

I attached a hub to the second port.

I have a Windows 7 client plugged into the hub.

"This setup was working on 2003 Server, now trying Ubuntu"

I followed the directions on the ubuntu site to setup Nat.
  	 	 	 	 	 	  [FONT=Courier New, serif][SIZE=3]**GUI Method via Network Manager (Ubuntu 9.10 and up).**[/SIZE][/FONT]


[FONT=Courier New, serif][SIZE=3]**I cannot connect.**[/SIZE][/FONT]


[FONT=Courier New, serif][SIZE=3]**Help.**[/SIZE][/FONT]


[FONT=Courier New, serif][SIZE=3][B]Thanks.
[/B][/SIZE][/FONT]

---

### Post by emunson on 2011-05-07
I currently have NAT working on an 11.04 install, though I followed instructions I found via google and cannot locate now however there is a post here that details the instructions:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Just for reference, here is the iptables script I run for NAT (I have removed some of the information from the script):
```

#!/bin/bash

#iptables based firewall, adjust the variables to match your
#network setup and desired open ports

WAN=[your WAN (the adapter talking to the outside world) adapter name (eg eth0)]
LAN=[your LAN (the one talking to the inside) adapter name (eg eth1, wlan0, or br0 for a bridge)]

WANIP=`ifconfig $WAN | awk \
        /$WAN/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`

#These lists contain the ports that will be open to accepting connections on
#$WAN.  Add any ports for services you want to expose.
TCP_PORTS="port list"
UDP_PORTS="port list"

iptables --flush
iptables --table nat --flush
iptables --delete-chain

iptables -A PREROUTING -t nat -p tcp -d $WANIP --dport [external port] -m state \
        --state NEW,ESTABLISHED,RELATED -j DNAT --to [internal address:port]

#Setup NAT IP forwarding and Masquerading
iptables --table nat --append POSTROUTING -o $WAN -j MASQUERADE
iptables --append FORWARD -i $LAN -j ACCEPT

#Set the types of packets/connections we will accept from WAN
iptables --append INPUT -i $WAN -m state --state ESTABLISHED,RELATED -j ACCEPT

#Open the listed ports
for PORT in $TCP_PORTS
do
        iptables --append INPUT -p tcp -i $WAN --dport $PORT -j ACCEPT
done

for PORT in $UDP_PORTS
do
        iptables --append INPUT -p udp -i $WAN --dport $PORT -j ACCEPT
done

#Set default policies, we drop everything incoming from the outside world and
#accept anything from inside
iptables --append INPUT -i $LAN -j ACCEPT
iptables --append INPUT -i lo -j ACCEPT
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD ACCEPT
iptables --policy INPUT DROP

```

---

### Post by Christloves on 2011-05-07
Thanks for your quick reply.  I shall work on this and post the results as soon as possible.

Thanks again.

---

