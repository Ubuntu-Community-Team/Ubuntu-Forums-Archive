---
title: "Port Forwarding"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Doug_M on 2010-05-05
Hi,

I have Adobe's Version Cue running in a VM.  I don't have control of the router the host server is on but it is in a DMZ.  So I want to use port forwarding to direct incoming packets on port 3703 to the VM.  I've been trying things like this:

```
iptables -t nat -A PREROUTING -p tcp --dport 3703 -j DNAT --to 172.16.124.128:3703

and

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3703 -j DNAT --to 172.16.124.128:3703

and

 
iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.1.69 --dport 3703 -j DNAT --to 172.16.124.128:3703
```

each time starting with "flushed" rules.  When I try connecting from a remote machine (in a browser) there is no response.  When I try telnetting from the host console to the eth0 address and port 3703 I get connection refused (yes I can telnet to the dest addr and port).  IP forwarding is set in sysctl.conf too I might add.  I'm obviously missing something here...

Thanks,
Doug

---

