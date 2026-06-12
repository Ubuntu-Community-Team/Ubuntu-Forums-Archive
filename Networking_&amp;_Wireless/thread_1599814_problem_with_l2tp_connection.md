---
title: "problem with l2tp connection"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by yakoza on 2010-10-18
i'm using gprs to connect to the internet and i wanna use vpn

with gprs i have to use l2tp connection that's way i've installed kvpnc on ubuntu(gnome)
but i get  error

this is kvpnc log
```


info: Gateway hostname (server1.vpn4irani.cz.cc) resolved to "217.23.11.234".
debug: Default interface: "ppp0".
debug: IP address of default interface: "10.5.148.69".
debug: Default interface: ppp0
debug: Local IP address: 10.5.148.69
debug: Local IP address (virtual): 10.5.148.69
debug: Local netmask (virtual): 32
debug: tmppath: /root/.kde/share/apps/kvpnc/
debug: Using NAT-T.
debug: Setting DNS_UPDATE "NO".
debug: Default interface: "ppp0".
debug: IP address of default interface: "10.5.148.69".
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: Username: naser
debug: "setkey" started.
debug: [racoon]: setkey finished.
debug: racoon: /usr/sbin/racoon -f /root/.kde/share/apps/kvpnc//racoon.naser2.conf
info: racoon started. 
debug: "/usr/bin/tail -f /root/.kde/share/apps/kvpnc/racoon.naser2.log" started.
debug: Policy was successful activated and daemon (racoon) is running, starting up tunnel...
error: [racoon err raw] racoon: failed to parse configuration file.
error: [racoon tail err] 2010-10-16 15:04:06: ERROR: /root/.kde/share/apps/kvpnc/racoon.naser2.conf:33: ";" algorithm mismatched
error: [racoon tail err] 2010-10-16 15:04:06: ERROR: fatal parse failure (1 errors)
error: Error in generated configuration file for "racoon", please contact the KVpnc team.
error: There is a reason to stop connecting, terminating "racoon" process.
debug: Disconnect requested
debug: Disconnect requested, status connecting
debug: Killing process while connecting. 
debug: [openl2tp] Starting /etc/init.d/openl2tpd...
debug: Stopping openl2tp...
error: Failed to start "ipsec".
debug: [openl2tp] Starting /etc/init.d/openl2tpd...
debug: Starting openl2tpd...
error: Failed to start "ipsec".
debug: route (racoon): route del default gw server1.vpn4irani.cz.cc ppp0
debug: [route err] cat: /root/.kde/share/apps/kvpnc//defaultroute_before.naser2: No such file or directory
debug: [route err] RTNETLINK answers: No such device
debug: [route err] 
debug: "iptables.naser2.remove_racoon.sh" started.
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: Disconnected.
error: [racoon err raw] 
error: There is a reason to stop connecting, terminating "racoon" process.
debug: Disconnect requested
debug: Not connected. 
debug: Disconnected.
error: [racoon err]: algorithm mismatched, please select another one.
error: There is a reason to stop connecting, terminating "racoon" process.
debug: Disconnect requested
debug: Not connected. 
debug: Disconnected.
error: Error in generated configuration file for "racoon", please contact the KVpnc team.
error: There is a reason to stop connecting, terminating "racoon" process.
debug: Disconnect requested
debug: Not connected. 
debug: Disconnected.
error: There is a reason to stop connecting, terminating "racoon" process.
debug: Disconnect requested
debug: Not connected. 
debug: Disconnected.
debug: "racoonctl vpn-connect 217.23.11.234" started.
error: [racoonctl err] racoonctl: cannot find source address
error: [racoonctl err] 

```and this is kvpnc's screenshot
[[IMG]http://www.freeimagehosting.net/uploads/th.bbb3761f9e.png[/IMG]]("http://www.freeimagehosting.net/image.php?bbb3761f9e.png")

---

### Post by yakoza on 2010-10-19
Buzz!

---

