---
title: "ADSL split routing IP masquerading problem"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ludichris on 2009-11-05
Greetings Ubuntu experts!

This is my first cry for help on your awesome facility. As a self-taught Linux user (with some FreeBSD training) I've found the answers to many of my questions here on your forums. Thanks a bunch for that.

Firstly, I'm running Ubuntu server 9.04 (jaunty). I have a local network (192.168.20.0/24) connected to interface eth0, an ADSL router (bridge mode) connected to a second interface (eth1 - 192.168.10.0/24). 

My server dials 3 PPPoE connections (ppp0, ppp1 and ppp2), each with its own purpose (0 is my international shaped account, 1 is my international unshaped account (for online gaming) and 2 is a SAIX local only account). I'm assuming you the readers are familiar with the applications of split routing in this context - if not I'm quite happy to explain. Anyway, i followed a guide posted at [http://tumbleweed.org.za/2008/09/19/split-routing-debianubuntu](http://tumbleweed.org.za/2008/09/19/split-routing-debianubuntu) to get as far as I am. 

I've installed and configured an iptables firewall, and IP masquerading for what i understand to be secure IPv4 forwarding.

In short, things are working, with the exception of a few things that are actually quite important. I can't seem to send mail (to a remote mail server that requires authentication to send mail - nothing special as far as I'm aware, i'm using default settings in Outlook, except i have configured it to use the incoming mail login details for sending mail). The strange thing is, when i "test account settings" in Outlook the test message is sent and received, but no other mail will send. 

Apart from this I also can't access a handful of websites that are very important in my current activities. If i had to guess, i'd say it's got something to do with secure data (everything works up until the point where you click on "log on", then after a few minutes of waiting i get a message stating "the connection to the server was interrupted", or sometimes "internal server error". An example of this is ABSA internet banking, although here i can log in and do most operations, but as soon as i click on "pay now" for any transaction, "connection to the server has been interrupted". Another example is the Stellenbosch university portal site at [http://www.mymaties.com]("http://www.mymaties.com/") where i am unable to get past the login screen without the abovementioned happening. Also (as i just found out) the same thing happens when i click "submit thread" on this forum. "Waiting for ubuntuforums.org" for a few minutes, followed by "Internal Server Error". 
If i connect one of my machines directly to my router and establish the pppoe connection straight on the PC, everything works great. 
Anyway, I'm no expert - i'm not even sure what logs or config files to supply. 
I'll start with my firewall script (/etc/network/if-up.d/00-firewall)

```

#!/bin/sh

PATH=/usr/sbin:/sbin:/bin:/usr/bin

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -i ! ppp+ -j ACCEPT
iptables -A FORWARD -i ppp+ -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow outgoing connections from the LAN side
iptables -A FORWARD -i eth0 -o ppp+ -j ACCEPT

# Masquerade.
iptables -t nat -A POSTROUTING -o ppp+ -j MASQUERADE

```Please let me know what else you require to help me troubleshoot this.

Kindest regards,
Chris Nightingale

---

### Post by ludichris on 2009-11-05
Here is the script that sets up the routing:

/etc/ppp/ip-up.d/routing

```

#!/bin/sh -e

case "$PPP_IFACE" in
 "ppp0")
   IFACE="webafrica-shaped"
   ;;
 "ppp1")
   IFACE="webafrica-unshaped"
   ;;
 "ppp2")
   IFACE="webafrica-local"
   ;;
 *)
   exit 0
esac

# Custom routes
if [ -f "/etc/network/routes-$IFACE" ]; then
  cat "/etc/network/routes-$IFACE" | while read route; do
    ip route add "$route" dev "$PPP_IFACE"
  done
fi

# Clean out old rules
ip rule list | grep "lookup $IFACE" | cut -d: -f2 | xargs -L 1 -I xx sh -c "ip rule del xx"

# Source Routing
ip route add "$PPP_REMOTE" dev "$PPP_IFACE" src "$address" table "$IFACE"
ip route add default via "$PPP_REMOTE" table "$IFACE"
ip rule add from "$PPP_LOCAL" table "$IFACE"

# Make sure this interface is present in all the custom routing tables:
route=`ip route show dev "$PPP_IFACE" | awk '/scope link  src/ {print $1}'`
awk '/^[0-9]/ {if ($1 > 0 && $1 < 250) print $2}' /etc/iproute2/rt_tables | while read table; do
  ip route add "$route" dev "$PPP_IFACE" table "$table"
done

```

The files refenced in this script exist, and according the netstat -rn all routes are set up correctly. Online gaming is working great and all traffic supposed to be going out via the local only interface and the international interface appears to be working as intented.

---

