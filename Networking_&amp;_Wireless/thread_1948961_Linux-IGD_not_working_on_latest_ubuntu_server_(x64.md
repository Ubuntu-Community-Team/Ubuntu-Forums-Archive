---
title: "Linux-IGD not working on latest ubuntu server (x64)"
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by Megapearl on 2012-03-29
Hello,

After upgrading to ubuntu server 11.10 (GNU/Linux 3.0.0-17-server x86_64) linux-igd stopped working and is not routing between interfaces.

eth0 is setup using dhcp (EXT interface WAN), and eth1 has a static ip address. (INT interface LAN)

Errors in syslog are:
```

upnpd[10408]: Failure obtaining ip address of interface eth0

```

Lots of Additional errors in upnpd.log are:
```

2012-03-29 12:38:09 0x7F51129BA700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:38:09 0x7F51131BB700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:35 0x7F51131BB700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:35 0x7F51129BA700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:35 0x7F51131BB700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:36 0x7F51129BA700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:42 0x7F51131BB700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:42 0x7F51129BA700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:42 0x7F51131BB700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL
2012-03-29 12:39:42 0x7F51129BA700 upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL

```

my /etc/default/linux-igd
```

# Defaults for linux-igd initscript
# sourced by /etc/init.d/linux-igd
# installed at /etc/default/linux-igd by the maintainer scripts

# Options for upnpd

# External interface name.  If undefined then upnpd will not be started.
EXTIFACE=eth0

# Internal interface name.  If undefined then upnpd will not be started.
INTIFACE=eth1

# Options for initscript

# Setup multicast route ?
# "yes" = add/del route to 224.0.0.0 through internal interface when starting/stopping daemon,
# "no" or unset = leave as-is, I will configure multicast routing by another method.
#ALLOW_MULTICAST=yes

# Options for start-stop-daemon

# User or user:group to run upnpd as, if not root.  This user will need
# suitable capabilities (I believe this is CAP_NET_ADMIN; untested).
# If undefined then upnpd will run as root.
#UPNPD_USER=$NAME:$NAME

# Supplementary group to run as (beyond those normally defined for
# UPNPD_USER).  If undefined then upnpd will run with the groups defined
# for the user, or if UPNPD_USER is also undefined then as gid=root.
#UPNPD_GROUP=$NAME

# Chroot directory (you need to maintain the chroot yourself with a program
# like 'jailer').  If undefined then upnpd will not be chrooted before starting.
#CHROOT_DIR=/var/chroot/$NAME

```

my /etc/upnpd.conf
```

# To change the interfaces used edit:
#   /etc/default/linux-igd

#
# The full path and name of the iptables executable,
# (enclosed in quotes).
#
iptables_location = "/sbin/iptables"

#
# Daemon debug level. Messages are logged via syslog to debug.
# 0 - no debug messages
# 1 - log errors
# 2 - log errors and basic info
# 3 - log errors and verbose info
# default = 0
debug_mode = 1

#
# Should the daemon create rules in the forward chain, or not.
# This is necessary if your firewall has a drop or reject
# policy in your forward chain.
# allowed values: yes,no
# default = no
create_forward_rules = yes

#
# Should the daemon insert or append rules in the forward chain.
# Normally you will want to insert rules at the beginning of the
# forward chain, so that they apply before any drop or reject rules
# later in the chain.
# This option only applies if "create_forward_rules = yes".
#
# As an experiment, this setting now also affects the PREROUTING chain
# in the same way.  If this causes you problems please let me (Debian
# maintainer) know through the BTS.
#
# Tip: If you need to insert rules somewhere in the middle of the PREROUTING
# or FORWARD chains, instead of first or last, then you should create a
# new empty chain, e.g forwardUPnP, and set forward_chain_name to that
# chain. Then insert a rule to jump to forwardUPnP in the appropriate place
# in the PREROUTING or FORWARD chain. (The value of forward_rules_append
# probably won't matter much in that case.)
#
# allowed values: yes,no
# default = no
forward_rules_append = no

#
# The name of the chain to put the forward rules in.
# This option only applies if "create_forward_rules = yes".
# allowed values: a-z, A-Z, _, -
# default = FORWARD
#
forward_chain_name = forwardUPnP
#forward_chain_name = FORWARD

#
# The name of the chain to put prerouting rules in.
# allowed values: a-z, A-Z, _, -
# default = PREROUTING
prerouting_chain_name = UPnP
#prerouting_chain_name = PREROUTING

#
# The internet line upstream bit rate reported from
# the daemon. Value in bits per second
# default = 0
upstream_bitrate = 512000

#
# The internet line downstream bit rate reported from
# the daemon. Value in bits per second
# default = 0
downstream_bitrate = 512000

#
# The default duration of port mappings, used when the client
# doesn't specify a duration.
# Can have the following values:
# 0 - no default duration specified
# seconds | HH:MM - duration from the time of addition
# @seconds | @HH:MM - expire mapping at the specified time of day
# default = 0
#duration = 86400 # One day from time of addition
duration = 21600

# The name of the igd device xml description document
# default = gatedesc.xml
description_document_name = gatedesc.xml

# The path to the xml documents
# Do not include the trailing "/"
# default = /etc/linuxigd
# WARNING! The make install does put the xml files
# in /etc/linuxigd, if you change this variable
# you have to make sure the xml docs are in the
# right place
xml_document_path = /etc/linuxigd

# The UPnP port to listen on.
# default = 0 (first free UPnP port, starting with 49152)
listenport = 0

# paranoid forwarding option
# 0, allow all forwarding
# 1, only allow internal hosts to forward to themselves.
# default = 0
paranoid = 1

# libupnp debug log file name
#  Note, if this file is enabled then linux-igd debug entries will also be
#  written to it as well as to syslog (see debug_mode, above)
upnp_log_filename = "/var/log/upnpd.log";

# libupnp debug logging level
#  UPNP_CRITICAL
#  UPNP_PACKET
#  UPNP_INFO
#  UPNP_ALL
upnp_log_level = UPNP_CRITICAL

```

What could be wrong here?
Is this a bug of linux-igd or ubuntu server?
Any help would be appreciated,

Regards,
Donald.

---

### Post by Megapearl on 2012-04-15
No one?

---

### Post by cmsdloma on 2013-02-26
I just got this working.  Do you have an IP Address for both eth0 and eth1?  Or does your external (WAN) interface eth0 use PPP to connect?  If so, then eth0 itself won't have an IP Address, and you have you specify ppp0 as the external interface.  That was the case for me.

Hope it helps, albeit a year late... :)

---

### Post by Megapearl on 2013-06-05
> **cmsdloma said:**
> I just got this working.  Do you have an IP Address for both eth0 and eth1?  Or does your external (WAN) interface eth0 use PPP to connect?  If so, then eth0 itself won't have an IP Address, and you have you specify ppp0 as the external interface.  That was the case for me.

Hope it helps, albeit a year late... :)

Just saw my own post when googling for linux-igd upnp and "upnpapi.c:3390 GetHandleInfo: HandleTable[2] is NULL"
Still got this same errors, now using ubuntu server 12.10, and latest upnpd.
My eth0 interface is assigned by dhcp via cablemodem. so that wasn't the issue for me...

Regards...

---

