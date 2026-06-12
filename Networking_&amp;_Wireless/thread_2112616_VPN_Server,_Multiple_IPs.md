---
title: "VPN Server, Multiple IPs"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by redtube98 on 2013-02-05
I have a question, and I really have no clue how to do this, I ordered a VPS with ubuntu, and ordered 5 ips, I want to make it so when a user connects with a different username/pw their assigned a different ip (external ip). I think I have to use ip tables, anyone know anything else?

---

### Post by TheFu on 2013-02-05
> **redtube98 said:**
> I have a question, and I really have no clue how to do this, I ordered a VPS with ubuntu, and ordered 5 ips, I want to make it so when a user connects with a different username/pw their assigned a different ip (external ip). I think I have to use ip tables, anyone know anything else?

I know of no way to accomplish this except to tell the users which IP address to use.
There may be a way to limit which IP a user may connect onto, but that will be extremely specific to the exact VPN software you deploy.

Do you have the machine listening on all IPs today? Usually the only reason to do this is if you must use the same inbound port, like 443, for SSL connections. However, if the same service is provided on the same port, then there is no need for multiple IPs.  If you can use multiple ports, like you can for a VPN service, then there really is not anything to be gained by having multiple IPs from a bandwidth or performance standpoint without having multiple NICs in the server.

---

### Post by redtube98 on 2013-02-05
> **TheFu said:**
> I know of no way to accomplish this except to tell the users which IP address to use.
There may be a way to limit which IP a user may connect onto, but that will be extremely specific to the exact VPN software you deploy.

Do you have the machine listening on all IPs today? Usually the only reason to do this is if you must use the same inbound port, like 443, for SSL connections. However, if the same service is provided on the same port, then there is no need for multiple IPs.  If you can use multiple ports, like you can for a VPN service, then there really is not anything to be gained by having multiple IPs from a bandwidth or performance standpoint without having multiple NICs in the server.

Well I could do that, whatever is the easiest, basically I want one VPS with VPN software that can use multiple ips, sorry for my lack of lingo lol

---

### Post by TheFu on 2013-02-05
> **redtube98 said:**
> Well I could do that, whatever is the easiest, basically I want one VPS with VPN software that can use multiple ips, sorry for my lack of lingo lol

VPN software setup is non-trivial. You need to know the "lingo."
If you care about security, then **do not** use PPTP.  Select from:

[LIST]
[*]IPSec
[*]L2TP
[*]OpenVPN
[/LIST]
Any of them can support multiple IPs or multiple users on 1 IP or multiple ports for multiple users on 1 or more IPs.


IPSec is built-into IPv6 which all current OSes support, so that is probably the easiest to use, provided you understand IPv6. IPSec also has implementations on IPv4.


You have some work to do.

---

