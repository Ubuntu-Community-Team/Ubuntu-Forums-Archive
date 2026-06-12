---
title: "I can't connect to my pptp ubuntu server"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by Atienza on 2010-12-06
Hi, I need your help to make work correctly my
pptp server with ubuntu 10.04.01 LTS cause:
I can connect from my windows client (XP and Vista)
but I can't connect from my ubuntu 10.04 LTS client

I've installed pptp server with

```
sudo aptitude install pptpd
```

then I edited the "/etc/pptpd.conf" configuration file:

```


# TAG: option
#       Specifies the location of the PPP options file.
#       By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#       Turns on (more) debugging to syslog
#
debug
# TAG: stimeout
#       Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#       Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#       Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
localip 192.168.1.253
remoteip 192.168.1.100-150

```

I edited the "/etc/ppp/pptpd-options" file:

```

# Authentication

# Name of the local system for authentication purposes
# (must match the second field in /etc/ppp/chap-secrets entries)
name pptpd

# Optional: domain name to use for authentication
# domain mydomain.net

# Strip the domain prefix from the username before authentication.
# (applies if you use pppd with chapms-strip-domain patch)
#chapms-strip-domain


# Encryption
# Debian: on systems with a kernel built with the package
# kernel-patch-mppe >= 2.4.2 and using ppp >= 2.4.2, ...
# {{{
refuse-pap
#refuse-chap
#refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
require-mschap-v2
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
require-mppe-128
# }}}


# Network and Routing

# If pppd is acting as a server for Microsoft Windows clients, this
# option allows pppd to supply one or two DNS (Domain Name Server)
# addresses to the clients.  The first instance of this option
# specifies the primary DNS address; the second instance (if given)
# specifies the secondary DNS address.
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2
ms-dns 192.168.1.254

# If pppd is acting as a server for Microsoft Windows or "Samba"
# clients, this option allows pppd to supply one or two WINS (Windows
# Internet Name Services) server addresses to the clients.  The first
# instance of this option specifies the primary WINS address; the
# second instance (if given) specifies the secondary WINS address.
#ms-wins 10.0.0.3
#ms-wins 10.0.0.4

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.  This will have the effect of making the peer appear to other
# systems to be on the local ethernet.
# (you do not need this if your PPTP server is responsible for routing
# packets to the clients -- James Cameron)
proxyarp

# Debian: do not replace the default route
nodefaultroute


# Logging
# Enable connection debugging facilities.
# (see your syslog configuration for where pppd sends to)
debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp

noipx
mtu 1490
mru 1490

```

I tried to connect from my ubuntu client with 
the network-manager, checking the:
"Use Point-to-point encryption (MPPE)"
but the connection fail

Any suggestion?

---

