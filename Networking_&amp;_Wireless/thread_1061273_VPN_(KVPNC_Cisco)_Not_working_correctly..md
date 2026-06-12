---
title: "VPN (KVPNC /Cisco) Not working correctly."
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by urbn on 2009-02-05
Afternoon folks.  I wasn't sure if this would be the correct discussion for this problem, but I figured VPN would fall into networking :)

The problem I am having is specific to my Ubuntu install.  I have connected too the same VPN for the last 5 years and varified on my XP machine (using the Cisco VPN Client) that the connect is up and running fine.

The problem that is occuring is KVpnc connects just fine, and will allow me too access files, run terminal service, and access FTP etc for a few minutes, but after this the connection is "lost".  KVpnc is still running and does not report a connection loss.  I can stop/start KVpnc and the connection will run fine again but only for a few minutes.

Anyone have any idea as to what I can try?  I"ve been trying too resolve this problem for a few hours and have changed many settings around.

current settings are:
use connection status check (disabled)
Reconnect after connection lost (disabled)
(note I have tired with both enabled, with different time amounts)

Debug log is :

debug: vpnc: /usr/sbin/vpnc
info: Gateway hostname (*.*.*.*) resolved to "*.*.*.*".
debug: vpnc version (major): "0"
debug: vpnc version (minor): "5"
debug: vpnc version (subminor): "1"
debug: VpncScript: /root/.kde/share/apps/kvpnc/vpnc-script.profilename 
debug: Support for TUN/TAP found (compiled into kernel or kernel module already loaded).
debug: Using NAT-T mode "natt".
debug: Using UDP.
info: Trying to connect to server "*.*.*.*" (*.*.*.*) with user "username" and IPSec ID "username"... 
debug: Setting DNS_UPDATE "Yes".
debug: "vpnc" started.
success: [vpnc] Connection established.
success: Successful connected to server: "*.*.*.*", user: "username", IPSec ID: "profile" at Thu Feb 5 13:51:12 2009 [Cisco (free)]
debug: [vpnc] Tunnel IP: 
debug: setFirewallAfterConnectScript: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.profile 
debug: "SetFirewallAfterConnectScript" started.
debug: "SetFirewallAfterConnectScript" finished.


debug: Disconnect requested
debug: Disconnect requested, status connected
debug: SetFirewallBeforeDisconnect: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.profile 
debug: "setFirewallBeforeDisconnect" started.
debug: "setFirewallBeforeDisconnect" finished.
debug: No vpnc pid file found, using "killall" for killing vpnc.
success: Successful disconnected.
info: Connection duration was 00 hours, 06 minutes, 40 seconds
[COLOR="Red"]error: [disconnect err] SIOCDELRT: No such process[/COLOR]

---

### Post by ja6a on 2010-02-07
Hi,

Try setting the MTU to 1300. This is the default MTU value set by CISCO. 
After starting the vpn connection you probably get an interface called tun0.
ifconfig tun0

change the MTU with this command:

sudo ifconfig tun0 mtu 1300

Doesn't fix it for me but is a start.

Also if it works well in windows try looking at:
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters\ Interfaces\[Adapter ID]

ref: ([http://www.gerzic.net/docs/vpnc-tips.txt](http://www.gerzic.net/docs/vpnc-tips.txt))

---

### Post by ja6a on 2010-02-07
Hi 

I was using tsclient to connect. When I switched to grdesktop the problem went away.

I think tsclient was upsetting vpnc in someway.

Cheers

---

