---
title: "the vpn connection &quot;vpn connection1&quot;  failed because the service failed to start"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by yugi_oh on 2010-12-12
Hello All

I got this error for two  days.back then I googled this error and i got some information about log file in /var/log/syslog
but i couldn't find it in google at all .
any help will appriciated.
this is all i got from syslog . look at the red paragraph

Dec 12 13:42:39 smolarek-Extensa-5635G NetworkManager[998]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Dec 12 13:42:39 smolarek-Extensa-5635G NetworkManager[998]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 13574
Dec 12 13:42:39 smolarek-Extensa-5635G NetworkManager[998]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Dec 12 13:42:39 smolarek-Extensa-5635G NetworkManager[998]: <info> VPN plugin state changed: 1
Dec 12 13:42:40 smolarek-Extensa-5635G NetworkManager[998]: <info> VPN plugin state changed: 3
Dec 12 13:42:40 smolarek-Extensa-5635G NetworkManager[998]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Dec 12 13:42:40 smolarek-Extensa-5635G NetworkManager[998]: [COLOR="Red"]<warn> VPN connection 'VPN connection 1' failed to connect: 'property 'progname=nm-pptp-auth-dialog; RGBA=on' invalid or not supported'.[/COLOR]
Dec 12 13:42:40 smolarek-Extensa-5635G NetworkManager[998]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 12 13:42:40 smolarek-Extensa-5635G NetworkManager[998]: <info> Policy set 'Auto DL-1' (wlan0) as default for IPv4 routing and DNS.

---

### Post by Arsic on 2010-12-13
This usually happens to me when I have the "Available to all users" box checked off.

---

