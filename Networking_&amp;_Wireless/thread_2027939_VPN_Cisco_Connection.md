---
title: "VPN Cisco Connection"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by hereimran on 2012-07-17
After successfully connected to VPN. When I tried to have access to a remote computer using "ssh -l username@server" i am getting an error 
"Could not resolve hostname "server": Name or service not known"

Can anyone help me in accessing the remote computer via VPN cisco.

Thanks

---

### Post by lukeiamyourfather on 2012-07-17
The -l argument is redundant but not the issue. Are you literally using that command or have you replaced "server" with an actual hostname? Are you able to ping the machine by hostname?

```
ping 192.168.1.18
```
```
ping data8
```

If you can't ping the machine by hostname then there's a network issue. For example the DNS isn't working or there simply isn't a DNS.

---

