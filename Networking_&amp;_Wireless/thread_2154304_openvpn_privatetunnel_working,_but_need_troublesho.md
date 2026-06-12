---
title: "openvpn privatetunnel working, but need troubleshooting help"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by sjl127 on 2013-06-14
I configured through the gui network manager.  It connects and works.  

My problem is when I power on the computer.  Wifi connects.

I have to   

```
 sudo /etc/init.d/openvpn stop      
```

 to get any internet access.  Then, I can connect through the network manager, as well.

What am I missing?  Thanks!

---

### Post by sjl127 on 2013-06-14
Solved.  

/etc/default/openvpn

AUTOSTART="none"

```
# This is the configuration file for /etc/init.d/openvpn

#
# Start only these VPNs automatically via init script.
# Allowed values are "all", "none" or space separated list of
# names of the VPNs. If empty, "all" is assumed.
# The VPN name refers to the VPN configutation file name.
# i.e. "home" would be /etc/openvpn/home.conf
#
#AUTOSTART="all"
AUTOSTART="none"
#AUTOSTART="home office"
#
# Refresh interval (in seconds) of default status files
# located in /var/run/openvpn.$NAME.status
# Defaults to 10, 0 disables status file generation
#
STATUSREFRESH=10
#STATUSREFRESH=0
# Optional arguments to openvpn's command line
OPTARGS=""
#
# If you need openvpn running after sendsigs, i.e.
# to let umountnfs work over the vpn, set OMIT_SENDSIGS
# to 1 and include umountnfs as Required-Stop: in openvpn's
# init.d script (remember to run insserv after that)
#
OMIT_SENDSIGS=0
```

---

