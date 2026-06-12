---
title: "OpenVPN help for beginner! PLEASE!"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by mxndrwgrdnr on 2011-12-07
Hate to beg, but I'm lost. Trying to set up an OpenVPN client to connect my laptop to the server in my office. I've installed openvpn on my machine, and have the .crt, .key, and .ovpn files for my office's server, but have no idea what do now. ANY help would be greatly appreciated.
thanks
max

---

### Post by dmizer on 2011-12-08
Have you installed network-manager-openvpn? If not, please install it. Then, you can configure your VPN client via the network tool in your panel.

Click on the networking icon, select "VPN connections" and "Configure VPN"
The "Network Connections" window will open to the VPN tab. Click "import" and browse to the directory where your ovpn file is located and select the ovpn file. Fill in your username and password if necessary, and click "apply"

Once you have that finished, you can start your VPN connection by clicking on your VPN name listed under "VPN connections" in your network icon.

---

