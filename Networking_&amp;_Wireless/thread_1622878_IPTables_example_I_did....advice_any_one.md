---
title: "IPTables example I did....advice any one?"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by taseedorf on 2010-11-16
This is something I am doing for school.  I am wondering if anyone has any input into what I have written.  Thanks!

# Big Pharm's IPTables Policy
# 
# Written and Composed by Tim Seedorf
#
# This assumes a few things.  
# Our headquarters has an IP of 66.24.234.223
# We use two DNS servers from our ISP; 69.123.127.158 and 69.123.128.158
# Internal Network Consists of many things, but...
# 
# Webserver resides at 192.168.1.110
# SSH server resides at 192.168.1.121
# SQL server resides at 192.168.1.132
# VPN server resides at 192.168.1.143
#
##############
# The Basics #
##############
#
# Turn on traffic filtering 
*filter 
#
# Default policies 
:INPUT DROP
:FORWARD DROP
# I want to allow most websites, just not the trouble some ones.
:OUTPUT ACCEPT
#
# Accept all traffic from the loopback interface. 
-A INPUT -i lo -j ACCEPT
#
# Accept legitimate responses to traffic we generate. 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
#
# Allow established traffic
-A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
#
#############################
# Services We Want to Allow #
#############################
#
# VPN 
iptables -A INPUT -p gre -j ACCEPT
iptables -A OUTPUT -p gre -j ACCEPT
iptables -A INPUT -p tcp --sport 1723 -s 192.168.1.143 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -d 192.168.1.143 -j ACCEPT
#
# Allow ssh (only from our headquarters)
iptables -A INPUT -s 66.24.234.223 -p tcp --dport ssh -j ACCEPT
#
# Allow web traffic
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
#
#
# Allow inbound DNS responses from our ISPs DNS servers. 
-A INPUT -s 69.123.128.158 -i eth0 -p udp -m state --state ESTABLISHED -m udp --sport 53 -j ACCEPT 
-A INPUT -s 69.123.128.158 -i eth0 -p tcp -m tcp --sport 53 -m state --state ESTABLISHED -j ACCEPT 
-A INPUT -s 69.123.127.158 -i eth0 -p udp -m state --state ESTABLISHED -m udp --sport 53 -j ACCEPT 
-A INPUT -s 69.123.127.158 -i eth0 -p tcp -m tcp --sport 53 -m state --state ESTABLISHED -j ACCEPT 
#
##########################################
# Connections We Want to Explicitly Deny #
##########################################
#
# 
#
###################
# Outbound Policy #
###################
#
# Naughty people try to visit websites while working
#
iptables -A OUTPUT -d facebook.com -j DROP
iptables -A OUTPUT -d myspace.com -j DROP
iptables -A OUTPUT -d twitter.com -j DROP
iptables -A OUTPUT -d digg.com -j DROP
iptables -A OUTPUT -d thepiratebay.com -j DROP
#
# 
###################
# Everything Else #
###################
#
# Drop Everything Else
iptables -A INPUT -j DROP
#
# Log Traffic
iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
#
# Make it all true. 
COMMIT

---

