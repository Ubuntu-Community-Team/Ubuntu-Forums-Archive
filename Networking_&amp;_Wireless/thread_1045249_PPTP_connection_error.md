---
title: "PPTP connection error"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2009-01-20
Hi,

I've set up a simple VPN using PPTP on our creeky old 6.06 LTS server, using a simple guide located here:

[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

Virtually all of our clients are XP and Vista and they can all connect without a problem. However, I'm running Intrepid (was Hardy) and can't connect.

From Intrepid, I'm connecting using PPTP. The IP address for the connection is correct (must be as I'm getting signs of a connection on the server... logs further down), as are the username and password (I've checked them against the secrets file). I've left everything else at the default (compression etc), but only after trying to change them all and testing each permutation.

Here's the pptpd.options file:

```
###############################################################################
# $Id: pptpd-options 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop PPP options file /etc/ppp/pptpd-options
# Options used by PPP when a connection arrives from a client.
# This file is pointed to by /etc/pptpd.conf option keyword.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 and the kernel MPPE module.
###############################################################################


# Authentication

# Name of the local system for authentication purposes 
# (must match the second field in /etc/ppp/chap-secrets entries)
name ChamonixServer

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
refuse-chap
refuse-mschap
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
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2
ms-dns 192.168.0.1

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
#debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp
auth
```

and the relevant section from syslog:

```
Jan 20 15:34:16 localhost pptpd[18123]: CTRL: Client 92.233.171.118 control connection started
Jan 20 15:34:18 localhost pptpd[18123]: CTRL: Starting call (launching pppd, opening GRE)
Jan 20 15:34:18 localhost pppd[18124]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jan 20 15:34:18 localhost pptpd[18123]: GRE: Bad checksum from pppd.
Jan 20 15:34:18 localhost pppd[18124]: pppd 2.4.4b1 started by root, uid 0
Jan 20 15:34:18 localhost pppd[18124]: Using interface ppp0
Jan 20 15:34:18 localhost pppd[18124]: Connect: ppp0 <--> /dev/pts/1
Jan 20 15:34:18 localhost pptpd[18123]: GRE: Received too short packet from pppd.
Jan 20 15:34:20 localhost pppd[18124]: MPPE required but peer refused
Jan 20 15:34:20 localhost pppd[18124]: Connection terminated.
Jan 20 15:34:20 localhost pppd[18124]: Connect time 0.1 minutes.
Jan 20 15:34:20 localhost pppd[18124]: Sent 18 bytes, received 36 bytes.
Jan 20 15:34:20 localhost pppd[18124]: Exit.
Jan 20 15:34:20 localhost pptpd[18123]: GRE: read(fd=6,buffer=80505c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Jan 20 15:34:20 localhost pptpd[18123]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Jan 20 15:34:20 localhost pptpd[18123]: CTRL: Reaping child PPP[18124]
Jan 20 15:34:20 localhost pptpd[18123]: CTRL: Client 92.233.171.118 control connection finished
```

Any ideas, folks?

---

### Post by taifu on 2009-02-15
Hi,

I have same kinda issue. I have setup PPTP server and always I get GRE: Bad checksum from pppd error when client try to connect what is may going to wrong?

---

### Post by RayVad on 2009-03-04
Same problem here. After certain time i got disconected and log shows same GRE Input/output error. 
Running Hardy Heron (8.04) here.

Any progress on your side about this problem?

---

### Post by IainPurdie on 2009-03-04
> **RayVad said:**
> Any progress on your side about this problem?

None, I'm afraid. I've been pretty much internet-less in Myanmar for a couple of weeks and it's slumped down my "to do" list. It's weird as I only get the issue when connecting with my Ubuntu install. Same laptop in Windows... no problem.

---

