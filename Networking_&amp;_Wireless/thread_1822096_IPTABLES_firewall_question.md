---
title: "IPTABLES firewall question"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by rng on 2011-08-10
I am using my computer for web browsing only and no other network related work. For this I am using following short script to provide a firewall. All FORWARD and INPUT traffic is blocked except that related to existing connections. However, all OUTPUT is allowed and browsing is not possible if I make OUTPUT to DROP as a policy, even if I accept OUTPUT to port 80 (www), 443 (https) and 53 (DNS).

Is it possible to keep OUTPUT to DROP as a policy after allowing for access to some ports? I need to permit only web browsing from network. 


#==============================================
#! /bin/bash

#Remove any existing rules from all chains
	iptables --flush
	iptables -t nat --flush
	iptables -t mangle --flush
#remove_user_chains:
	iptables -X
	iptables -t nat -X
	iptables -t mangle -X

#set default policy to drop
	iptables --policy INPUT DROP
	iptables --policy FORWARD DROP
	iptables --policy OUTPUT ACCEPT	

#unlimited traffic on loopback interface
	iptables -A INPUT -i lo -j ACCEPT

# Allow previously established connections
        iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT 
#============================================

---

