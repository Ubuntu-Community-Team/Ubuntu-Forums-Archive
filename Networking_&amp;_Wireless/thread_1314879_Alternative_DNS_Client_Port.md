---
title: "Alternative DNS Client Port"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by johndoe32102002 on 2009-11-04
I am trying to add a DNS server to Ubuntu that does not utilize the default port 53.  How is this possible in Ubuntu? Irc.ubuntu.com #ubuntu was uncertain this was possible.  Adding a host <dns_server_ip>:<port> failed to work in Ubuntu 9.10.  I wish to do this on the client side, not the server side (server is setup with a non-port 53 port).

One makeshift suggestion was:
ssh -2 -4 -N -T -R remotehost:5353:localhost:53
//substitute 5353 for the remote dns port

Another suggestion would be temporarily editing the /etc/resolv.conf  But this would change upon reboot.

There should be a easier way to do this.

---

### Post by mpokrywka on 2009-11-05
Of course there is simplier solution: use iptables DNAT.

```
iptables -t nat -D OUTPUT -d remote_dns_ip -p udp --dport 53 -j DNAT --to remote_dns_ip:5353
```

---

### Post by johndoe32102002 on 2009-11-08
A simple way would be to add this capability natively into to Ubuntu.  Thanks though for the command; I may use it when it because necessary.

---

