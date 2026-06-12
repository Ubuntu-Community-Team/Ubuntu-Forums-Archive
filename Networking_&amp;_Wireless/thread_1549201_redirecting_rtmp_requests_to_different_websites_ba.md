---
title: "redirecting rtmp requests to different websites based on host name"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2010-08-09
I am looking for a layer 7 firewall.I have to redirect rtmp requests for different hostnames coming at a gateway to internal servers at LAN at their respective hostnames.
If some one has some idea let me know can this be done on IPTABLES
via 
```
IPTABLES incoming at port 1935 -protocol rtmp -hostname1 to server 1 on LAN @ port 1935
IPTABLES incoming at port 1935 -protocol rtmp -hostname2 to server 2 on LAN @ port 1935

```like that.
Or if not IPTABLES then some other feasible solution.

---

