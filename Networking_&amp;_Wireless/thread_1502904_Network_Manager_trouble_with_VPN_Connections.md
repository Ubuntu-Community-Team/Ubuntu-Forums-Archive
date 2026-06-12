---
title: "Network Manager trouble with VPN Connections"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by cdecker on 2010-06-06
Hi all,

I'm having a bit of trouble with the network manager under Ubuntu 9.10, specifically I tried a VPNC, OpenVPN and a PPTP connection but none work. Looking at the syslog I find this:
> Jun  6 12:17:57 legio NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun  6 12:17:57 legio NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 25998
Jun  6 12:17:57 legio NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun  6 12:17:57 legio NetworkManager: nm-vpn-connection.c.828: NeedSecrets failed: dbus-glib-error-quark Rejected send message, 1 matched rules; type="method_call", sender=":1.1" (uid=0 pid=959 comm="NetworkManager) interface="org.freedesktop.NetworkManager.VPN.Plugin" member="NeedSecrets" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.pptp" (uid=0 pid=25998 comm="/usr/lib/network-manager-pptp/nm-pptp-service))
Jun  6 12:17:57 legio NetworkManager: <WARN>  connection_state_changed(): Rejected send message, 1 matched rules; type="method_call", sender=":1.1" (uid=0 pid=959 comm="NetworkManager) interface="org.freedesktop.NetworkManager.VPN.Plugin" member="Disconnect" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.pptp" (uid=0 pid=25998 comm="/usr/lib/network-manager-pptp/nm-pptp-service))
Jun  6 12:17:57 legio NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
Jun  6 12:17:57 legio NetworkManager: <info>  Policy set 'Auto ZickenWG' (wlan0) as default for routing and DNS.
So I guess it's a problem with DBUS, but I have no idea as to why.

Any ideas?

---

