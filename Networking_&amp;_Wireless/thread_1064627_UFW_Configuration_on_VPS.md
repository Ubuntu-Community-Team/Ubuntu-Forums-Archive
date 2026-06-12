---
title: "UFW Configuration on VPS"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by martin1977 on 2009-02-09
I'm carring out two parallel installs of Ubuntu 8.04 LTS 32bit, both web/mail servers.  One is a 'home' server installed using the alternate CD and installation/configuration of ufw was a breeze!

On the other, a Xen virtual private server, installation of ufw has not gone well and I would appreciate some help.

The first problem was that installing ufw immediately locked me out on port 22 and I had to get access back to the server from the vps HyperVM control panel.  

I then added the rules that I needed (same as the home server), but found that I had slow login on SSH, ping not working etc and had to disable ufw

Here's some information on diagnosis I've already done and errors on enabling ufw.  I suspect problems with the vps kernel or ipv6, but really this is beyond my level of skills on Linux.  I can get rid of the module errors by disabling them in /etc/default/ufw.

Can someone suggest a solution?

Regards, Martin

The server:

root@vps:~# uname -a
Linux [fqdn removed] 2.6.18-92.1.22.el5xen #1 SMP Tue Dec 16 12:26:32 EST 2008 x86_64 GNU/Linux

Errors on start-up of ufw:

root@vps:~# ufw enable
ERROR: problem running init script
root@vps:~# ufw enable
Firewall started and enabled on system startup

root@vps:~# /etc/init.d/ufw force-reload
 * Stopping firewall: ufw...                                             [ OK ]
 * Starting firewall: ufw...                                                    
FATAL: Module nf_conntrack_ftp not found.
FATAL: Module nf_nat_ftp not found.
FATAL: Module nf_conntrack_irc not found.
FATAL: Module nf_nat_irc not found.
iptables-restore: line 71 failed
 * Problem running '/etc/ufw/before.rules'...                                   
iptables-restore: line 31 failed
 * Problem running '/etc/ufw/after.rules'...                             [fail]
 
root@vps:~# ufw status
Firewall loaded
 
To                         Action  From
--                         ------  ----
22:tcp                     ALLOW   Anywhere
80:tcp                     ALLOW   Anywhere
443:tcp                    ALLOW   Anywhere
443:udp                    ALLOW   Anywhere
993:tcp                    ALLOW   Anywhere
993:udp                    ALLOW   Anywhere
995:tcp                    ALLOW   Anywhere
995:udp                    ALLOW   Anywhere
25:tcp                     ALLOW   Anywhere
10000:tcp                  ALLOW   Anywhere
37:tcp                     ALLOW   Anywhere
37:udp                     ALLOW   Anywhere
53:tcp                     ALLOW   Anywhere
53:udp                     ALLOW   Anywhere

Syslog:

Feb  9 06:50:09 vps kernel: ip_tables: conntrack match: invalid size 80 != 68
Feb  9 06:50:09 vps kernel: ip_tables: limit match: invalid size 40 != 28

Configuration files:

# /etc/default/ufw
# 

# set to yes to apply rules to support IPv6 (no means only IPv6 on loopback
# accepted). You will need to 'disable' and then 'enable' the firewall for
# the changes to take affect.
IPV6=no

# set the default input policy to ACCEPT or DROP.  Please note that if you
# change this you will most likely want to adjust your rules
DEFAULT_INPUT_POLICY="DROP"

# set the default output policy to ACCEPT or DROP.  Please note that if you
# change this you will most likely want to adjust your rules
DEFAULT_OUTPUT_POLICY="ACCEPT"

# set the default forward policy to ACCEPT or DROP.  Please note that if you
# change this you will most likely want to adjust your rules
DEFAULT_FORWARD_POLICY="DROP"

#
# IPT backend
#
# only enable if using iptables backend
IPT_SYSCTL=/etc/ufw/sysctl.conf

# extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"

# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=yes

sysctl.conf
#
# Configuration file for setting network variables
#

# uncomment this to allow this host to route packets between interfaces
#net/ipv4/ip_forward=1
#net/ipv6/conf/default/forwarding=1

net/ipv4/conf/all/rp_filter=1
net/ipv4/conf/default/rp_filter=1

net/ipv4/conf/all/accept_source_route=0
net/ipv4/conf/default/accept_source_route=0
net/ipv6/conf/all/accept_source_route=0
net/ipv6/conf/default/accept_source_route=0

net/ipv4/conf/all/accept_redirects=0
net/ipv4/conf/default/accept_redirects=0
net/ipv6/conf/all/accept_redirects=0
net/ipv6/conf/default/accept_redirects=0

net/ipv4/conf/all/log_martians=0
net/ipv4/conf/default/log_martians=0

net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_echo_ignore_all=0
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/tcp_syncookies=0

#net/ipv4/tcp_fin_timeout=30
#net/ipv4/tcp_keepalive_intvl=1800

# normally allowing tcp_sack is ok, but if going through OpenBSD 3.8 RELEASE or
# earlier pf firewall, should set this to 0
net/ipv4/tcp_sack=1

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -i lo -j ACCEPT

# connection tracking rules
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets
# uncomment to log INVALID packets
#-A ufw-before-input -m conntrack --ctstate INVALID -j LOG --log-prefix "[UFW BLOCK INVALID]: "
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP

# connection tracking for outbound
-A ufw-before-output -p tcp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK NOT-TO-ME]: "

# all other non-local packets are dropped
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

#
# rules.input-after
#
# Rules that should be run after the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-after-input
#   ufw-after-output
#   ufw-after-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-after-input - [0:0]
:ufw-after-output - [0:0]
:ufw-after-forward - [0:0]
# End required lines

# don't log noisy services by default
-A ufw-after-input -p udp --dport 137 -j RETURN
-A ufw-after-input -p udp --dport 138 -j RETURN
-A ufw-after-input -p tcp --dport 139 -j RETURN
-A ufw-after-input -p tcp --dport 445 -j RETURN
-A ufw-after-input -p udp --dport 67 -j RETURN
-A ufw-after-input -p udp --dport 68 -j RETURN

# catchall for logging
-A ufw-after-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK INPUT]: "
-A ufw-after-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK FORWARD]: "

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

---

### Post by martin1977 on 2009-02-09
More output:

root@vps:~# ufw version
ufw 0.16.2.4

root@vps:~# ufw default deny
ERROR: problem running init script

Corresponding Syslog:

Feb  9 08:48:18 vps kernel: ip_tables: conntrack match: invalid size 80 != 68

root@vps:~# ip6tables -L INPUT
ip6tables v1.3.8: can't initialize ip6tables table `filter': Bad file descriptor
Perhaps ip6tables or your kernel needs to be upgraded.

Probably related:

[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/251355]("https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/251355")

---

### Post by martin1977 on 2009-02-11
Just an update - removed ufw and read up on iptables here:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Problem solved.

Regards, Martin

---

