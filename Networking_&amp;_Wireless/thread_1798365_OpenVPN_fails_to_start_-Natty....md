---
title: "OpenVPN fails to start -Natty..."
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Nerotriple6 on 2011-07-06
Hey.

This is all over Google, 3 years ago it was reported as a bug in Ubuntu, Kubuntu and the lot. Google is full of this problem, but no solution!
I have my OpenVPN working in Windows and I imported my settings from there, didn't work, neither did making settings as instructed by my OpenVPN provider in Network Manager.

When attempting to connect I get a libnotify or whatever it is message:
[I]The VPN connection [name] failed to start
Connection was not provided by any settings service[/I]

I added the following to the conf file located in
**/etc/dbus-1/system.d/nm-openvpn-service.conf**
```
 <policy user="at_console"> 
            <policy user="at_console"> 
            <allow own="org.freedesktop.NetworkManager.vpnc"/> 
            <allow send_destination="org.freedesktop.NetworkManager.openvpn"/> 
        </policy>
```
That sorted out the OpenVPN service failing to start issue for my but it threw me straight into this issue, which doesn't appear to have a solution to it.

---

