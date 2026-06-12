---
title: "Connecting to Cisco IPsec VPN Fails in Jaunty"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by heypete on 2009-08-31
I'm running a fully up-to-date version of Ubuntu 9.04 Jaunty at the time of this post. It's a new install on this system.

My university offers a VPN service for students, staff, and faculty. According to the Cisco VPN client I use on my Windows systems, they use IPSec/UDP.

I am attempting to configure my Ubuntu system to connect to this VPN, as I am often off-campus. I have installed the **vpnc** and **network-manager-vpnc** packages.

The university has provided a .pcf configuration file which, when imported, appears to fill in all the appropriate fields in the network-manager configuration page. The proper host IP address, group name, group password, etc. all appear to be in order. The pull-down menu next to "group password" is set to "Saved", and the password is indeed saved.

The "User Name" and "Domain" fields remain blank. Encryption Method is "Secure (default)", and NAT Traversal is "Cisco UDP (default)".

However, when I attempt to connect to the VPN, I'm met with (I'm paraphrasing here, as I can't seem to get the errors to reappear at the moment) "Cannot connect to [network name]. Unable to get shared secrets." error messages. These messages only appear the first time one attempts to connect after logging in -- if one attempts it a second time, no errors are presented.

The following errors are presented in the syslog:
```
Aug 31 00:46:21 inara NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
Aug 31 00:46:21 inara NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 9480 
Aug 31 00:46:21 inara NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
Aug 31 00:46:21 inara NetworkManager: nm-vpn-connection.c.900: NeedSecrets failed: dbus-glib-error-quark Rejected send message, 1 matched rules; type="method_call", sender=":1.9" (uid=0 pid=2894 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo") interface="org.freedesktop.NetworkManager.VPN.Plugin" member="NeedSecrets" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.vpnc" (uid=0 pid=9480 comm="/usr/lib/network-manager-vpnc/nm-vpnc-service "))
Aug 31 00:46:21 inara NetworkManager: <WARN>  connection_state_changed(): Rejected send message, 1 matched rules; type="method_call", sender=":1.9" (uid=0 pid=2894 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo") interface="org.freedesktop.NetworkManager.VPN.Plugin" member="Disconnect" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.vpnc" (uid=0 pid=9480 comm="/usr/lib/network-manager-vpnc/nm-vpnc-service ")) 
Aug 31 00:46:21 inara NetworkManager: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
Aug 31 00:46:21 inara last message repeated 2 times
Aug 31 00:46:21 inara NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Aug 31 00:46:21 inara NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 31 00:46:33 inara NetworkManager: <debug> [1251704793.999524] ensure_killed(): waiting for vpn service pid 9480 to exit 
Aug 31 00:46:34 inara NetworkManager: <debug> [1251704793.999779] ensure_killed(): vpn service pid 9480 cleaned up 

```

Any suggestions or recommendations?

Cheers!
-Pete

**Update:** After a quick restart, everything appears to be working normally. My apologies for the noise.

---

### Post by jonobr on 2009-08-31
Hello


Not sure if this helps, but Im using VPNC with kvpnc as the front end.

That allows you to load in a pcf file from the gui.

Thats working for me using Jaunty and 0.9.0 kvpnc

---

