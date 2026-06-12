---
title: "can I let some services bypass my VPN?"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by gschoppe on 2013-01-03
I am connected to an OpenVPN service on my server, for security purposes.  I want all services that do not require authentication, such as bittorrent and all outgoing web surfing to use the VPN Tunnel to communicate.  however, the server needs to be remotely administered and accessed via WebMin, Qbittorrent's WebUI, FTP, and Subsonic, using the non-VPN interface.

I cannot base the filtering off IP address, as I do not know what IP I will always connect from.

How can I exempt specific protocols from the VPN?

---

### Post by gschoppe on 2013-01-06
...still looking for a solution.  I know split tunneling exists, but I have no idea how to implement by port, rather than by ip.

Help?

---

### Post by gschoppe on 2013-01-06
ok, so with some creative googling, I found the following command referenced:
```

iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dports [PORT#] -j dnat --to-destination [GATEWAY IP]

```

I don't know enough about it to be sure, but it seems to filter requests to a specific gateway by port.

Can I use this with OpenVPN?

---

