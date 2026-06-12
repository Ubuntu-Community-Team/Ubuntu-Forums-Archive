---
title: "only first of UDP broadcast clients receives data"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by S.G. on 2009-10-30
I'm trying some examples of broadcast UDP sockets using the Qt library.
For some reason, only the first cliend to bind to a port receives the data.
What can the problem be?

Thank you in advance.

---

Do I need to open the port to which clients bind themselves? I'm not aware of having any firewall... and I assume that if the port was closed the first client would be as unable to receive as the others, but there is something I'm missing somewhere.

---

I've tried to open the port (UDP 9988) like this:
```
 iptables -A INPUT -p udp --dport 9988 -j ACCEPT
```
and also:
```
/bin/echo "0" > /proc/sys/net/ipv/icmp_echo_ignore_broadcasts
```

Nothing works so far...

Any hint?

---------------

I had forgotten to update this. In fact the solution was in the Qt documentation.

> QUdpSocket::ShareAddress	Allow other services to bind to the same address and port. This is useful when multiple processes share the load of a single service by listening to the same address and port (e.g., a web server with several pre-forked listeners can greatly improve response time). However, because any service is allowed to rebind, this option is subject to certain security considerations. Note that by combining this option with ReuseAddressHint, you will also allow your service to rebind an existing shared address. On Unix, this is equivalent to the SO_REUSEADDR socket option. On Windows, this option is ignored.

QUdpSocket::DontShareAddressBind the address and port exclusively, so that no other services are allowed to rebind. By passing this option to QUdpSocket::bind(), you are guaranteed that on successs, your service is the only one that listens to the address and port. No services are allowed to rebind, even if they pass ReuseAddressHint. This option provides more security than ShareAddress, but on certain operating systems, it requires you to run the server with administrator privileges. On Unix and Mac OS X, not sharing is the default behavior for binding an address and port, so this option is ignored. On Windows, this option uses the SO_EXCLUSIVEADDRUSE socket option.

---

