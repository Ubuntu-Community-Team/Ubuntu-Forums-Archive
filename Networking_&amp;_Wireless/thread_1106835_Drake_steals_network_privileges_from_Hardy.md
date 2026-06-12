---
title: "Drake steals network privileges from Hardy?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by afrodeity on 2009-03-26
I've been having trouble with my router (TPLINK TD8840). Basically, I can't boot into it using default gateway of 196.168.1.1. with my computer which is running Hardy. Anyway, I installed Dapper Drake on a second computer, plugged it into the router, and no problem. Also, pages where I have to login and submit password ie Facebook and Wordpress are working fine on the Drake but not with the Hardy. What do you think is the problem? I've tried running pppoeconf, initially it said the package wasn't installed properly. So I reinstalled and went through the setup but nothing. Its still running the same. 

Here is my dsl-provider file:

# Configuration file for PPP, using PPP over Ethernet 
# to connect to a DSL provider.
#
# See the manual page pppd(8) for information on all the options.

##
# Section 1
#
# Stuff to configure...

# MUST CHANGE: Uncomment the following line, replacing the [email]user@provider.net[/email]
# by the DSL user name given to your by your DSL provider.
# (There should be a matching entry in /etc/ppp/pap-secrets with the password.)
#user [email]myusername@myprovider.net[/email]

# Use the pppoe program to send the ppp packets over the Ethernet link
# This line should work fine if this computer is the only one accessing
# the Internet through this DSL connection. This is the right line to use
# for most people.
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452"

# An even more conservative version of the previous line, if things
# don't work using -m 1452... 
#pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1412"

# If the computer connected to the Internet using pppoe is not being used
# by other computers as a gateway to the Internet, you can try the following
# line instead, for a small gain in speed:
#pty "/usr/sbin/pppoe -I eth0 -T 80"


# The following two options should work fine for most DSL users.

# Assumes that your IP address is allocated dynamically
# by your DSL provider...
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
# Comment out if you already have the correct default route installed.
defaultroute

##
# Section 2
#
# Uncomment if your DSL provider charges by minute connected
# and you want to use demand-dialing. 
#
# Disconnect after 300 seconds (5 minutes) of idle time.

#demand
#idle 300

##
# Section 3
#
# You shouldn't need to change these options...

hide-password
lcp-echo-interval 20
lcp-echo-failure 3
# Override any connect script that may have been set in /etc/ppp/options.
connect /bin/true
noauth
persist
mtu 1492

# RFC 2516, paragraph 7 mandates that the following options MUST NOT be
# requested and MUST be rejected if requested by the peer:
# Address-and-Control-Field-Compression (ACFC)
noaccomp
# Asynchronous-Control-Character-Map (ACCM)
default-asyncmap

plugin rp-pppoe.so eth0
user "XXXXXXX@telkomsa.net"

---

