---
title: "Getting &quot;No valid secrets&quot; when trying to connect"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by jancogo on 2010-07-13
I just reinstalled my laptop from 8 to 10.04. Everything works OK except OpenVPN (which worked fine before the reinstall). I'm using Gnome and have installed openvpn along with network-manager-gnome. When I have configured the connection (User and CA certificate and key) and try to connect it fails immediately with "The VPN connection <name> failed because there were no valid VPN secrets."

Here is some output from syslog after a failed attempt:

[FONT="Courier New"]Jul 13 12:57:42 aurora NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Jul 13 12:57:42 aurora NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 4655
Jul 13 12:57:42 aurora NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Jul 13 12:57:42 aurora NetworkManager: nm-vpn-connection.c.828: NeedSecrets failed: dbus-glib-error-quark Rejected send message, 1 matched rules; type="method_call", sender=":1.2" (uid=0 pid=881 comm="NetworkManager) interface="org.freedesktop.NetworkManager.VPN.Plugin" member="NeedSecrets" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.openvpn" (uid=0 pid=4655 comm="/usr/lib/network-manager-openvpn/nm-openvpn-servic"))
Jul 13 12:57:42 aurora NetworkManager: <WARN>  connection_state_changed(): Rejected send message, 1 matched rules; type="method_call", sender=":1.2" (uid=0 pid=881 comm="NetworkManager) interface="org.freedesktop.NetworkManager.VPN.Plugin" member="Disconnect" error name="(unset)" requested_reply=0 destination="org.freedesktop.NetworkManager.openvpn" (uid=0 pid=4655 comm="/usr/lib/network-manager-openvpn/nm-openvpn-servic"))
Jul 13 12:57:42 aurora NetworkManager: <info>  Policy set 'kitty' (wlan0) as default for routing and DNS.[/FONT]

---

### Post by Ruesca on 2010-07-19
For me a simple restart of the system helped!

see also [http://www.cjtreasurechest.com/blog/index.php/2009/05/ubuntu-904-the-vpn-connection-failed-because-there-were-no-valid-secrets/](http://www.cjtreasurechest.com/blog/index.php/2009/05/ubuntu-904-the-vpn-connection-failed-because-there-were-no-valid-secrets/)

cheers

---

### Post by upayavira on 2010-11-03
You can achieve the same thing with simply:

sudo /etc/init.d/network-manager restart

Upayavira

---

