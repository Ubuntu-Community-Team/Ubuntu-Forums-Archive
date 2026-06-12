---
title: "Shorewall not allowing other ports te open as 22"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by mrrepel on 2012-08-09
Hi all,

I have Ubuntu 11.04 desktop as server  at home for filesharing and incoming internet. I've installed:
- ISC DHCPd version 4.1.1 (working)
- BIND version 9.7.3
- Shorewall version 4.4.17

My server has 2 connections, ppp0 ( 3g modem, dynamic IP ) and eth0 ( local network ). My server is running on 10.42.43.1 internal.

I've used this guide to install shorewall:
[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001) and the help from the shorewall setup guide.

Shorewall works and i can acces what i want on my local network and have internet to my computers. I have a portforward stated in the rules section and this works to. I want to open ports 5555 ( webmin ) and 8000 ( VLC mms streaming server ) to the internet. This is the configuration i have:


interfaces:
```

#
# Shorewall version 4.0 - Sample Interfaces File for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-interfaces"
###############################################################################
#ZONE    INTERFACE    BROADCAST    OPTIONS
net     ppp0            -              dhcp,tcpflags,nosmurfs,routefilter,logmartians
loc     eth0            detect          tcpflags,nosmurfs,routefilter,logmartians

```policys
```

#
# Shorewall version 4.0 - Sample Policy File for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-policy"
###############################################################################
#SOURCE        DEST        POLICY        LOG LEVEL    LIMIT:BURST

loc        net        ACCEPT
net        all        DROP        info
$FW            net             ACCEPT
loc            $FW             ACCEPT
$FW            loc             ACCEPT
# THE FOLLOWING POLICY MUST BE LAST
all        all        REJECT        info

```masq
```
#
# Shorewall version 4.0 - Sample Masq file for two-interface configuration.
# Copyright (C) 2006 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.
#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-masq"
###############################################################################
#INTERFACE        SOURCE        ADDRESS        PROTO    PORT(S)    IPSEC    MARK
ppp0            10.0.0.0/8,\
            169.254.0.0/16,\
            172.16.0.0/12,\
            192.168.0.0/16

```Rules
```

#
# Shorewall version 4.0 - Sample Rules File for two-interface configuration.
# Copyright (C) 2006,2007 by the Shorewall Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# See the file README.txt for further details.

#------------------------------------------------------------------------------
# For information about entries in this file, type "man shorewall-rules"
###############################################################################$
#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE         $
#                                                       PORT    PORT(S)        $
#
#       Accept DNS connections from the firewall to the network
#
DNS(ACCEPT)     $FW             net
DNS(ACCEPT)     loc             $FW
ACCEPT          $FW             net                udp       53
ACCEPT          $FW             net                tcp       53
#
#       Accept SSH connections from the local network for administration
#
SSH(ACCEPT)     loc             $FW
#
#       Allow Ping from the local network
#
#
Ping(ACCEPT)    loc             $FW
#
# Drop Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping(DROP)      net             $FW

ACCEPT          $FW             loc             icmp
ACCEPT          $FW             net             icmp
#
#Portforward
DNAT            net             loc:10.42.43.100:80  tcp     8080
ACCEPT          net           $FW       tcp        22
ACCEPT          net             $FW     tcp     5555
ACCEPT          net             $FW     tcp     8000

```When i run 
```

sudo netstat -tanp | grep LISTEN | sort

```i get:
```

tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      814/sshd
tcp        0      0 0.0.0.0:5555            0.0.0.0:*               LISTEN      1771/perl
tcp6       0      0 :::8000                 :::*                    LISTEN      28207/vlc

```And lot's of other ports not worth mentioning.

I can acces the ssh server and  my portforward from "the outside". 5555 and 8000 seems to stay closed:

Online portscanner:
Scanning ports on 178.224.22.XXX

178.224.22.XXX is responding on port 22 (ssh).
178.224.22.XXX isn't responding on port 5555 (personal-agent).
178.224.22.XXX isn't responding on port 8000 (irdmi).
178.224.22.XXX is responding on port 8080 (webcache).

Does anybody have an idea why my ports aren't opening ?

Greets

MrRepel

---

