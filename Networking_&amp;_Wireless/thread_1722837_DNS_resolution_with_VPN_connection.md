---
title: "DNS resolution with VPN connection"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Sidrabs on 2011-04-06
Hello,

There is a OpenVPN server installed in our office, so I wanted to configure my Ubuntu 10.10 laptop to use this connection and enjoy all the benefits in comparison to clunky VNC remote connection.

The office router has a DNS service installed in it, what handles some local domain names for the test servers and other devices. For normal work, it would be nice to have them resolved also on my laptop, once the VPN connection is established.

Right now I can successfully establish the connection, and if I maintain the list of local domain names in my /etc/hosts file, all is fine. But that manual local hosts file maintenance feels like there could be better solution. I tried to put my office DNS server IP address in the VPN connection configuration, and then I get this behaviour that all the local domain names are properly resolved, but none of the external domain names. Once I disconnect the VPN connection, my external domain resolution is back.

What would be the proper config, to enjoy the special local domain name resolution, while in the VPN connection, without loosing normal external domain name resolution?

UPDATE: I am not sure what I messed up in the VPN connection setup, but  now my external domain resolution doesn't work any more, while in the  connection, despite the fact that it says Method: Automatic (VPN) in the IPv4 Sessings panel of the VPN config dialog.

---

