---
title: "vpnc drops, then cannot do any dns resolution"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by nickpdx on 2011-08-19
I'm running vpnc on 10.04 to connect to my company's Cisco VPN.  Every so often, vpnc drops silently.  I can reconnect, BUT after reconnect I can no longer resolve any DNS names.

What happens from my POV is:
* I see that vpnc is no longer running

* I can see that /etc/resolv.conf was reset back to its normal non-vpn state:
nameserver 192.168.0.1

* I restart vpnc, it states that it connected fine

* I can see that resolv.conf now includes my company's internal nameservers:
nameserver 192.168.4.10
nameserver 192.168.4.13
nameserver 192.168.0.1

* BUT I cannot connect to either of those IPs.  Cannot ping 192.168.4.10 or 4.13.  So all internal DNS lookups of course fail when resolution fails over to my router.

The route to 4.10/4.13 is broken or something?  What to do next or even how to troubleshoot that is out of my realm of experience.  I can see that the tun0 interface is up (ifconfig -a) and the stuff displayed there is the same as it looks when vpnc is running and everything's working fine.

---

### Post by nickpdx on 2011-08-19
When vpnc drops the vpn connection I think this is what gets logged:

Aug 19 10:45:34 foobox vpnc[6761]: connection terminated by dead peer detection
Aug 19 10:45:34 foobox vpnagent[1214]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1694 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Aug 19 10:45:35 foobox vpnagent[1214]: last message repeated 23 times
Aug 19 10:45:35 foobox NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 19 10:45:35 foobox vpnagent[1214]: A network interface has gone down.
Aug 19 10:45:35 foobox vpnagent[1214]: Function: logInterfaces File: RouteMgr.cpp Line: 2076 Invoked Function: logInterfaces Return Code: 0 (0x00000000) Description: IP Address Interface List: 192.168.0.2 FE80:0:0:0:213:2FF:FE77:4239  
Aug 19 10:45:35 foobox vpnagent[1214]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1694 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown

---

### Post by nickpdx on 2011-08-19
I also note that when I'm in this state of inability to connect to the nameservers, it does not help to disconnect vpnc, reestablish my network connection, and reconnect vpnc.  But it DOES help if I reboot my router.

Again, what to do with that information is outside of my experience.  Any tips would be helpful.

---

### Post by nickpdx on 2011-08-19
I was looking at the vpnc options and noticed that I can disable "DPD" which I guess stands for "dead peer detection".  Noting that in syslog it says it terminates vpnc due to dead peer detection.  So, I disabled it.  We'll see if that has any effect.

---

### Post by nickpdx on 2011-08-30
Anecdotal evidence is good so far that disabling Dead Peer Detection had a positive effect.

---

