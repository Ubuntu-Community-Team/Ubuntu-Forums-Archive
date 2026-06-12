---
title: "Is there a replacement for Firestarter?"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by kurtkraut on 2009-11-08
Firestarter is a discontinued project, [according to Wikipedia]("http://en.wikipedia.org/wiki/Firestarter_%28firewall%29"). I'd like to know if there is a replacement for Firestarter.

On IRC some people recomended me ufw+Gufw, what **doesn't** stands as a replacement for Firestarter in my opinion. Firestarter would appear with a red icon on tray **alerting** when something gets blocked by firewall, making you **instantly** aware of port scans, attacks or even if something useful is being blocked by mistake.

The Ubuntu [official documentation]("https://help.ubuntu.com/9.10/serverguide/C/firewall.html") also mentions another **discontinued project**, the [FireFlier]("http://fireflier.sourceforge.net/"), that also had the interactive approach Firestarter had.

So, what do we have for Ubuntu that could replace Firestarter on this area?

---

### Post by dvlchd3 on 2009-11-08
I use iptables+snort+base to get the same results.

For desktop use, I simply use the attached script in the /etc/network/if-up.d directory.  This allows me to do anything, while remaining rather invisible on the network. (Cannot ping, stealth scans take a long time, all ports closed unless I instigated a connection.)  The only thing I explicitly allow are DHCP broadcasts in both directions.

Snort+base will allow you to monitor any suspicious looking activity.  (And in much more detail than firestarter)

Beyond that, ufw is a great tool if iptables is something you can't/don't want to take the time to learn.

Best guide I've found on setting up snort and base:
[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

My firewall script:
```

#!/bin/bash

## Firewall script for BRICKMAN using iptables
## This script meant to be executed from /etc/network/if-up.d/
############################################################
# Copyright (C) 2009 Dan Buhrman
#
#  Permission to use, copy, modify, and distribute this software and its
#  documentation for educational, research, private and non-profit purposes,
#  without fee, and without a written agreement is hereby granted. 
#  This software is provided as an example and basis for individual firewall
#  development.  This software is provided without warranty.
#
#  Any material furnished by Dan Buhrman is furnished on an 
#  "as is" basis.  He makes no warranties of any kind, either expressed 
#  or implied as to any matter including, but not limited to, warranty 
#  of fitness for a particular purpose, exclusivity or results obtained
#  from use of the material.
#
# This script is based off of Robert Ziegler's rc.firewall script
###########################################################

# Get IP address since we are dynamically assigned it.
# Change wlan0 to your network interface:
IPADDR="`/sbin/ifconfig wlan0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"

# Remove any existing rules from all chains
iptables --flush
iptables -t nat --flush
iptables -t mangle --flush

# Set the default filter table policy
iptables --policy INPUT DROP
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD DROP

# Remove any pre-existing user-defined chains
iptables --delete-chain
iptables -t nat --delete-chain
iptables -t mangle --delete-chain

# Unlimited traffic on the loopback interface
iptables -A INPUT -i lo -j ACCEPT

#############################################################
# Using Connection State to By-pass Rule Checking

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#############################################################

###########################################################
# DHCP tests must precede broadcast-related rules, as DHCP relies
# on broadcast traffic initially.

iptables -A INPUT -p udp -s 0.0.0.0 --sport 67 \
	-d 255.255.255.255 --dport 68 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
	-d 255.255.255.255 --dport 68 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
	--dport 68 -j ACCEPT
iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
	-d $IPADDR --dport 68 -j ACCEPT

##########################################################

```

---

### Post by kurtkraut on 2009-11-08
> **dvlchd3 said:**
> I use iptables+snort+base to get the same results.


I appreciate your suggestion but don't we have something more **desktop oriented** than this? I'm more concerned of having a product replacement for Firestarter (for Ubuntu community) than having its functionally by a self implementation or shell scripting.

---

