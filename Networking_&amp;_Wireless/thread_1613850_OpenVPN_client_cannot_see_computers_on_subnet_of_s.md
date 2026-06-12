---
title: "OpenVPN client cannot see computers on subnet of server"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by rafter109 on 2010-11-04
I have a VPN setup with an Ubuntu 10.04 VPN server, an Ubuntu 10.04 client, and a Windows 7 client. VPN server is on network 192.168.1.0 and clients are on network 192.168.0.0. When connecting to the VPN server with the Ubuntu client, I cannot ping or otherwise communicate with other computers on the server's subnet but I CAN ping and share files when connected with the Windows 7 machine. Anyone ran into this before? I can post configs, logs, etc. if anyone can assist me. Thanks in advance.

---

### Post by rafter109 on 2010-11-05
polite bump

---

### Post by rafter109 on 2010-11-05
anybody?

---

### Post by SeijiSensei on 2010-11-08
Try adding this to the Ubuntu client:

In the client's OpenVPN .conf file include the directive:

```
up ./add_routes
```

Then in /etc/openvpn create the add_routes file as root with this line:

```
ip route add 192.168.1.0/24 via ip.addr.of.vpn
```

replacing "ip.addr.of.vpn" with the IP address of the server's end of the VPN link.  E.g., if you use the OpenVPN directive:

```
ifconfig 10.10.10.1 10.10.10.2
```

you'd replace with "ip.addr.of.vpn" with "10.10.10.2".

Make the script executable by the root user with "chmod u+x /etc/openvpn/add_routes".

---

