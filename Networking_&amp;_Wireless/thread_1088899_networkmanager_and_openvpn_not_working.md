---
title: "networkmanager and openvpn not working"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by vavoem on 2009-03-06
when i try to log on to my openvpn server with the normal openvpn client i have no problem but the client in networkmanager comes up with the following error 

Could not start the VPN connection 'lappie@home' due to a connection error.

The VPN login failed because the VPN program could not connect to the VPN server.

i have searched an googled and found some people who say it might be a problem with the client in networkmanager but they are all pretty old posts does anyone have an idea if this problem was allready solved? or better yet how to solve it 
hardy heron 8.04
nm-applet 0.6.6
nm-openvpn installed

excerpt from syslog private info xx-ed out

Mar  6 20:15:24 eeepc NetworkManager: <info>  Will activate VPN connection 'lappie@home', service 'org.freedesktop.NetworkManager.openvpn', user_name 'xxxxxxx', vpn_data 'connection-type / shared-key / dev / tun / remote / xxxxxxx / port / xxx / proto / tcp-client / servercert-insecure / no / ca /  / cert /  / key /  / comp-lzo / yes / shared-key / /etc/openvpn/static.key / local-ip / 10.8.0.2/24 / remote-ip / 10.8.0.1/24 / username / ', route ''. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 1 of 4 (Connection Prepare) scheduled... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.openvpn (PID 11443) 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 1 of 4 (Connection Prepare) complete. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 1 -> 6. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 2 of 4 (Connection Prepare Wait) complete. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 3 of 4 (Connect) scheduled... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 3 of 4 (Connect) sending connect request. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 6 -> 3. 
Mar  6 20:15:24 eeepc nm-openvpn[11446]: Options error: Parameter ns_cert_type can only be specified in TLS-mode, i.e. where --tls-server or --tls-client is also specified.
Mar  6 20:15:24 eeepc nm-openvpn[11446]: Use --help for more information.
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 3 of 4 (Connect) reply received. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN Activation (lappie@home) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Mar  6 20:15:24 eeepc NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.openvpn', signal 'ConnectFailed', with message 'The VPN login failed because the VPN program could not connect to the VPN server.'. 
Mar  6 20:15:24 eeepc NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' signaled state change 3 -> 6. 
Mar  6 20:15:24 eeepc NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.openvpn): could not stop connection 'lappie@home' because service was 6.

---

### Post by vavoem on 2009-03-15
Bump

---

### Post by vavoem on 2009-03-25
BUMP yet again

---

