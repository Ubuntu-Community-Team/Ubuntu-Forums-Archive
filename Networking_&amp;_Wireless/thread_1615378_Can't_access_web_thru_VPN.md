---
title: "Can't access web thru VPN"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by acidblue on 2010-11-06
I've set up A VPN (pptpd)server on 10.04 using this guide;
[http://sysadmingeek.com/articles/setting-up-a-vpn-pptp-server-on-debian/](http://sysadmingeek.com/articles/setting-up-a-vpn-pptp-server-on-debian/)

I can connect to the VPN server from my Debian 6 laptop but I can't access the web, I get a "Cannot resolve hostname error".
I've set ipforwarding, but is that enough?
Do I need to install a DNS server as well?

Her are my config files:
pptpd-options:
###############################################################################
# $Id: pptpd-options 4643 2006-11-06 18:42:43Z rene $
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
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2

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
    ms-dns 192.168.1.1

    nobsdcomp

    noipx

    mtu 1490

    mru 1490

---

### Post by acidblue on 2010-11-06
This is my pptpd.conf file.
seems easier to read if I split my conf files into 2 posts.

###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#	Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#	Specifies the location of the PPP options file.
#	By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#	Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#	Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#	Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#	Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#	Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#	You can specify single IP addresses seperated by commas or you can
#	specify ranges, or both. For example:
#
#		192.168.0.234,192.168.0.245-249,192.168.0.254
#
#	IMPORTANT RESTRICTIONS:
#
#	1. No spaces are permitted between commas or within addresses.
#
#	2. If you give more IP addresses than MAX_CONNECTIONS, it will
#	   start at the beginning of the list and go until it gets 
#	   MAX_CONNECTIONS IPs. Others will be ignored.
#
#	3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#	   you must type 234-238 if you mean this.
#
#	4. If you give a single localIP, that's ok - all local IPs will
#	   be set to the given one. You MUST still give at least one remote
#	   IP for each simultaneous client.
#
# (Recommended)
 localip 192.168.1.122
 remoteip 192.168.1.234-238,192.168.1.245
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245

---

### Post by acidblue on 2010-11-07
[bump]>

---

### Post by SeijiSensei on 2010-11-08
I haven't set up pptpd in quite a while, but I think you need to point the "ms-dns" directives to the IP addresses of the DNS servers you're using internally.

If both the client and server are running *nix, though, I'd suggest [OpenVPN]("http://openvpn.net") as a much simpler solution than pptpd.  OpenVPN also has a Windows implementation in case you need to support Windows clients as well.

---

### Post by acidblue on 2010-11-08
> **SeijiSensei said:**
> I haven't set up pptpd in quite a while, but I think you need to point the "ms-dns" directives to the IP addresses of the DNS servers you're using internally.

If both the client and server are running *nix, though, I'd suggest [OpenVPN]("http://openvpn.net") as a much simpler solution than pptpd.  OpenVPN also has a Windows implementation in case you need to support Windows clients as well.

So not the DNS on the router?
So putting a DNS on the same server as the VPN is that what your suggesting, or at least the same network.

If I use Open VPN i don't need DNS ?
Here is how I have my network:
Cable modem>>router>>VPN server/workstation.

My understanding is you can use the DNS on the router to resolve host-names. But that is for host-names on the network not internet.

Forgive my ignorance but this is all a bit new to me.

---

### Post by SeijiSensei on 2010-11-08
If you have an internal private network behind a firewall, you need to run an internal DNS server to resolve local names.  That doesn't seem to be your problem, though.  Your Debian client can't resolve names out on the Internet it appears.

If you're using your router as a DNS server, then try entering the router's internal IP address to the "ms-dns" entry in the pptpd configuration file.

The other option is to configure DNS resolution manually on the Debian client.  Edit the file /etc/resolv.conf on that machine.  You should see some "nameserver" entries.  Make sure the first nameserver entry points to the internal IP address of the router. This may not persist, though, if the Debian machine uses DHCP to get its DNS server information along with an IP address.  That's why I'd try the ms-dns option in pptpd first. 

What is the contents of the VPN server's /etc/resolv.conf?  I presume that if you sit in front of that box and open a browser you can see remote websites?  If so, just make sure the Debian client has the same first nameserver entry as the VPN server itself.

---

### Post by acidblue on 2010-11-08
>  
What is the contents of the VPN server's /etc/resolv.conf?  I presume that if you sit in front of that box and open a browser you can see remote websites?  If so, just make sure the Debian client has the same first nameserver entry as the VPN server itself.

```
# Generated by NetworkManager
nameserver 192.168.1.1
```
Yes I can surf the web from the VPN server.

>  If you're using your router as a DNS server, then try entering the router's internal IP address to the "ms-dns" entry in the pptpd configuration file.


Do you mean the routers LAN IP or WAN IP
I have it set to the LAN IP, which 198.162.1.1

---

### Post by SeijiSensei on 2010-11-08
Yes, the LAN IP.  Did you try that?  What happened?

Perhaps you're better off just adding that "nameserver" line manually to the client's /etc/resolv.conf.

---

### Post by acidblue on 2010-11-08
> **SeijiSensei said:**
> Yes, the LAN IP.  Did you try that?  What happened?

Perhaps you're better off just adding that "nameserver" line manually to the client's /etc/resolv.conf.

I've always had ms-dns to the LAN IP, thats why i was kinda stumped when it didn't work, oh well.

I'm going to give OpenVPN a try if setting the clients resolve.conf doesn't work, I might just try it anyway.

---

### Post by alcapone-g on 2013-03-04
If you connect to remote computer using vpn, your internet access comes from remote computer you are connected with vpn. Your computer lose direct acces to internet in a moment you create working vpn connection. If remote computer does not have its own internet connection and you connected to it using vpn you lose your access to internet.

---

