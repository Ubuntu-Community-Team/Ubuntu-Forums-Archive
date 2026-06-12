---
title: "PPTP Server Gateway"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by linuxman94 on 2012-07-09
I am attempting to set up a pptpd server with Ubuntu 12.04 Server (64bit) that will act as a gateway.  For some reason, I have not been able to get it to work correctly.

Here is my pptpd.conf:

```
###############################################################################
# $Id$
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#    Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#    Specifies the location of the PPP options file.
#    By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#    Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#    Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#    Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#    Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#    Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#    You can specify single IP addresses seperated by commas or you can
#    specify ranges, or both. For example:
#
#        192.168.0.234,192.168.0.245-249,192.168.0.254
#
#    IMPORTANT RESTRICTIONS:
#
#    1. No spaces are permitted between commas or within addresses.
#
#    2. If you give more IP addresses than MAX_CONNECTIONS, it will
#       start at the beginning of the list and go until it gets 
#       MAX_CONNECTIONS IPs. Others will be ignored.
#
#    3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#       you must type 234-238 if you mean this.
#
#    4. If you give a single localIP, that's ok - all local IPs will
#       be set to the given one. You MUST still give at least one remote
#       IP for each simultaneous client.
#
# (Recommended)
localip 192.168.5.10
remoteip 192.168.5.15
#or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245

```pptpd-options:
```
###############################################################################
# $Id$
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
auth

```options:
```
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specif which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Severs can be remotely configured
ms-dns 8.8.8.8
ms-dns 8.8.4.4

# Specify which WINS Servers the incoming connection Win95 or WinNT should use
# ms-wins 192.168.1.50
# ms-wins 192.168.1.51

# Run the executable or shell command specified after pppd has
# terminated the link.  This script could, for example, issue commands
# to the modem to cause it to hang up if hardware modem control signals
# were not available.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

# async character map -- 32-bit hex; each bit is a character
# that needs to be escaped for pppd to receive it.  0x00000001
# represents '\x01', and 0x80000000 represents '\x1f'.
asyncmap 0

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth
# ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

# Use hardware flow control (i.e. RTS/CTS) to control the flow of data
# on the serial port.
crtscts

# Use software flow control (i.e. XON/XOFF) to control the flow of data
# on the serial port.
#xonxoff

# Specifies that certain characters should be escaped on transmission
# (regardless of whether the peer requests them to be escaped with its
# async control character map).  The characters to be escaped are
# specified as a list of hex numbers separated by commas.  Note that
# almost any character can be specified for the escape option, unlike
# the asyncmap option which only allows control characters to be
# specified.  The characters which may not be escaped are those with hex
# values 0x20 - 0x3f or 0x5e.
#escape 11,13,ff

# Don't use the modem control lines.
#local

# Specifies that pppd should use a UUCP-style lock on the serial device
# to ensure exclusive access to the device.
lock

# Don't show the passwords when logging the contents of PAP packets.
# This is the default.
hide-password

# When logging the contents of PAP packets, this option causes pppd to
# show the password string in the log message.
#show-password

# Use the modem control lines.  On Ultrix, this option implies hardware
# flow control, as for the crtscts option.  (This option is not fully
# implemented.)
modem

# Set the MRU [Maximum Receive Unit] value to <n> for negotiation.  pppd
# will ask the peer to send packets of no more than <n> bytes. The
# minimum MRU value is 128.  The default MRU value is 1500.  A value of
# 296 is recommended for slow links (40 bytes for TCP/IP header + 256
# bytes of data).
#mru 542

# Set the interface netmask to <n>, a 32 bit netmask in "decimal dot"
# notation (e.g. 255.255.255.0).
netmask 255.255.255.0

# Disables the default behaviour when no local IP address is specified,
# which is to determine (if possible) the local IP address from the
# hostname. With this option, the peer will have to supply the local IP
# address during IPCP negotiation (unless it specified explicitly on the
# command line or in an options file).
#noipdefault

# Enables the "passive" option in the LCP.  With this option, pppd will
# attempt to initiate a connection; if no reply is received from the
# peer, pppd will then just wait passively for a valid LCP packet from
# the peer (instead of exiting, as it does without this option).
#passive

# With this option, pppd will not transmit LCP packets to initiate a
# connection until a valid LCP packet is received from the peer (as for
# the "passive" option with old versions of pppd).
#silent

# Don't request or allow negotiation of any options for LCP and IPCP
# (use default values).
#-all

# Disable Address/Control compression negotiation (use default, i.e.
# address/control field disabled).
#-ac

# Disable asyncmap negotiation (use the default asyncmap, i.e. escape
# all control characters).
#-am

# Don't fork to become a background process (otherwise pppd will do so
# if a serial device is specified).
#-detach

# Disable IP address negotiation (with this option, the remote IP
# address must be specified with an option on the command line or in
# an options file).
#-ip

# Disable IPCP negotiation and IP communication. This option should
# only be required if the peer is buggy and gets confused by requests
# from pppd for IPCP negotiation.
#noip

# Disable magic number negotiation.  With this option, pppd cannot
# detect a looped-back line.
#-mn

# Disable MRU [Maximum Receive Unit] negotiation (use default, i.e.
# 1500).
#-mru

# Disable protocol field compression negotiation (use default, i.e.
# protocol field compression disabled).
#-pc

# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
#+chap

# Don't agree to authenticate using CHAP.
#-chap

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
#-vj

# Increase debugging level (same as -d).  If this option is given, pppd
# will log the contents of all control packets sent or received in a
# readable form.  The packets are logged through syslog with facility
# daemon and level debug. This information can be directed to a file by
# setting up /etc/syslog.conf appropriately (see syslog.conf(5)).  (If
# pppd is compiled with extra debugging enabled, it will log messages
# using facility local2 instead of daemon).
#debug

# Append the domain name <d> to the local host name for authentication
# purposes.  For example, if gethostname() returns the name porsche,
# but the fully qualified domain name is porsche.Quotron.COM, you would
# use the domain option to set the domain name to Quotron.COM.
#domain <d>

# Enable debugging code in the kernel-level PPP driver.  The argument n
# is a number which is the sum of the following values: 1 to enable
# general debug messages, 2 to request that the contents of received
# packets be printed, and 4 to request that the contents of transmitted
# packets be printed.
#kdebug n

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>

# Set the name of the local system for authentication purposes to <n>.
# This is a privileged option. With this option, pppd will use lines in the
# secrets files which have <n> as the second field when looking for a
# secret to use in authenticating the peer. In addition, unless overridden
# with the user option, <n> will be used as the name to send to the peer
# when authenticating the local system to the peer. (Note that pppd does
# not append the domain name to <n>.)
#name <n>

# Enforce the use of the hostname as the name of the local system for
# authentication purposes (overrides the name option).
#usehostname

# Set the assumed name of the remote system for authentication purposes
# to <n>.
#remotename <n>

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.
#proxyarp

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
# login

# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.
lcp-echo-interval 30

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.
lcp-echo-failure 4

# Set the LCP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#lcp-restart <n>

# Set the maximum number of LCP terminate-request transmissions to <n>
# (default 3).
#lcp-max-terminate <n>

# Set the maximum number of LCP configure-request transmissions to <n>
# (default 10).
#lcp-max-configure <n>

# Set the maximum number of LCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#lcp-max-failure <n>

# Set the IPCP restart interval (retransmission timeout) to <n>
# seconds (default 3).
#ipcp-restart <n>

# Set the maximum number of IPCP terminate-request transmissions to <n>
# (default 3).
#ipcp-max-terminate <n>

# Set the maximum number of IPCP configure-request transmissions to <n>
# (default 10).
#ipcp-max-configure <n>

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#ipcp-max-failure <n>

# Set the PAP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#pap-restart <n>

# Set the maximum number of PAP authenticate-request transmissions to
# <n> (default 10).
#pap-max-authreq <n>

# Set the maximum time that pppd will wait for the peer to authenticate
# itself with PAP to <n> seconds (0 means no limit).
#pap-timeout <n>

# Set the CHAP restart interval (retransmission timeout for
# challenges) to <n> seconds (default 3).
#chap-restart <n>

# Set the maximum number of CHAP challenge transmissions to <n>
# (default 10).
#chap-max-challenge

# If this option is given, pppd will rechallenge the peer every <n>
# seconds.
#chap-interval <n>

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Disable the IPXCP and IPX protocols.
# To let pppd pass IPX packets comment this out --- you'll probably also
# want to install ipxripd, and have the Internal IPX Network option enabled
# in your kernel.  /usr/doc/HOWTO/IPX-HOWTO.gz contains more info.
noipx

# Exit once a connection has been made and terminated. This is the default,
# unless the `persist' or `demand' option has been specified.
#nopersist

# Do not exit after a connection is terminated; instead try to reopen
# the connection.
#persist

# Terminate after n consecutive failed connection attempts.
# A value of 0 means no limit. The default value is 10.
#maxfail <n>

# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.
#demand

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  Note: it is not advisable to use this option with the persist
# option without the demand option.  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
#idle <n>

# Specifies how many seconds to wait before re-initiating the link after
# it terminates.  This option only has any effect if the persist or demand
# option is used.  The holdoff period is not applied if the link was
# terminated because it was idle.
#holdoff <n>

# Wait for up n milliseconds after the connect script finishes for a valid
# PPP packet from the peer.  At the end of this time, or when a valid PPP
# packet is received from the peer, pppd will commence negotiation by
# sending its first LCP packet.  The default value is 1000 (1 second).
# This wait period only applies if the connect or pty option is used.
#connect-delay <n>

# Packet filtering: for more information, see pppd(8)
# Any packets matching the filter expression will be interpreted as link
# activity, and will cause a "demand" connection to be activated, and reset
# the idle connection timer. (idle option)
# The filter expression is akin to that of tcpdump(1)
#active-filter <filter-expression>

# ---<End of File>---

```I am able to connect to the VPN and get an IP address, however, I do not get a gateway and cannot connect to the internet.  I can also ping the IP of the machine running the VPN when I am connnected.

I also have enabled kernel ip forwarding.

---

### Post by poolet on 2012-07-09
/*uncommend ms-dns on etc/ppp/pptpd-options*/ 

```
# If pppd is acting as a server for Microsoft Windows clients, this
# option allows pppd to supply one or two DNS (Domain Name Server)
# addresses to the clients.  The first instance of this option
# specifies the primary DNS address; the second instance (if given)
# specifies the secondary DNS address.
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
ms-dns 10.0.0.1 
ms-dns 10.0.0.2 
```try to used 8.8.8.8 and 8.8.4.4 to utilize google DNS servers

did you set up ip-masquerading?? if no, 
```
sudo nano /etc/rc.local
# PPTP Forwarding
iptables -t nat -A POSTROUTING -o "interface" -j MASQUERAD
```E

at the end uncomment the line in
```
/etc/sysctl.conf:
net.ipv4.ip_forward=1
```reboot..
 just in case your vpn doesn't directly connect may need yo forwarded port 1723 TCP and GRE to the LAN IP of you VPN server 

please check the command:

iptables -L and make sure that you have check your iptables before you continue with changes. 

hope that helps you!!

**NOTE:: seems that you have point/uncommend  ms-dns in a wrong position::** ( but may am wrong I will confirm it for sure and I would let you know)

this is your conf
```
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specif which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Severs can be remotely configured
ms-dns 8.8.8.8
ms-dns 8.8.4.4
```

---

### Post by linuxman94 on 2012-07-09
I set the dns options in pptpd-options and restart pptpd. Nothing changes.
I have masquerading set.
net.ipv4.ip_forward is set to 1.
The ports are forwarded through my router.

---

### Post by poolet on 2012-07-10
Ok. to be sure that has nothing to do with provider, login in your modem and make a summarization  range for all ip address of locals ip's.
where localip is the address of the server, and remoteip the addresses that will handed out to the clients.

```
/etc/pptpd.conf[INDENT]localip 192.168.1.10
 remoteip 192.168.1.234-238,192.168.1.245
[/INDENT]
```at /etc/ppp/pptpd-options
at the end of the file put the following::[INDENT]```
ms-dns "**where ms-dns is the DNS server for the  local network**"
auth 
nobsdcomp
noipx
mtu 1490
mru 1490 

```[/INDENT]make a restart:: 
```
/etc/init.d/pptpd restart
```if the problem continues try to remove "auth" as your using at the end..and try again. seems weird of whats happen, but may your router isn't respond back correctly may there is something configure that isn't allowed the router to send respond back...

---

### Post by linuxman94 on 2012-07-10
I tried all of the above and it still isn't functioning as a gateway correctly.  My router (running DD-WRT) is set to allow PPTP pass-through and port 1723 is forwarded.  I also use ufw for configuring iptables but I don't see how that would cause a problem.

---

### Post by linuxman94 on 2012-07-10
Solved my own problem.  I had to set DEFAULT_FORWARD_POLICY in /etc/default/ufw to "ACCEPT"
Thanks for the help though.

---

