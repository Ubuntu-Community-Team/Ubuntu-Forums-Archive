---
title: "Routing traffic from workstation through vpn server"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by astbis on 2010-11-19
Hi

I am trying to figure out which is the best way to solve this problem.

One person is working on a laptop, which is connected to the internet through his private ISP connection. But the ISP is refusing to let SMTP traffic og any kind through. This way the only possibility to connect to email at work would be webmail.

My thought: Is it possible to redirect traffic or entire connection though an existing OpenVPN connection?

Regards,

---

### Post by SeijiSensei on 2010-11-19
What is the laptop running?  Linux? Windows? OS/X?  If it's Linux, you can try this approach.

I tunnel all the traffic between a workstation and my Linux external router to add an additional layer of security to the wifi connection it uses and to facilitate a couple of services that need to see the workstation directly.

It's a bit tricky to set up because you have to make sure you have a route to the VPN server so you can pass the traffic between them, but use the tunnel for everything else.

For reference, I'll post the script I use.  I run this after I've set up the connection to my wifi router at 192.168.1.1:

```

#!/bin/sh

# check to see if I have connected to the router
TEST=`ifconfig | grep 'inet addr:192.168.1'`

if [ "$TEST" != "" ]
then
    # add a route to the VPN router at 192.168.100.1 using the wifi connection
    ip route add 192.168.100.1 via 192.168.1.1
    
    # restart VPN to connect to the router and create the tunnel
    /etc/init.d/openvpn restart
    
    # repoint my default route to use the remote tunnel IP (10.100.1.1)
    ip route del default
    ip route add default via 10.100.1.1

fi

exit 0

```

When finished, my routing table looks like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
10.100.1.1      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         10.100.1.1      0.0.0.0         UG    0      0        0 tun0


```

---

### Post by SlugSlug on 2010-11-19
it is yer, but it may be easier to use the submission port 587..

---

