---
title: "SNMP monitoring"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2011-11-07
Hi all i have a SNMP server (prtg) and i want to be able to monitor the eth0 interface of a different server in my LAN (ubuntu server 11.04 64-bit).

i have had a google but none of the things i have tried have worked !

any ideas .......  

thanks

---

### Post by jonobr on 2011-11-07
Hi There,

The default port for SNMP is udp port 161

It requires the agent on the target device to be listening for a query.
What I would recommend is to check you PRTG is doing a query

You can test this on your machine by doing a trace
In a terminal
```
tcpdump -vvv -i any -s 1600 port 161
```

Do a query,

If you see  output on the terminal that should indicate the packet going out.

You should see  a response or responses coming back also

If you don't, either the query hit a machine which is not running an snmp agent , or the agent is not running, or their other machine is fire walled.

It could also be that your OID your using is not recognized, however, if the agent was running I would expect there to be some kind of response.

First things first though, run the trace and do the query
if you want help reading, you can post here

---

### Post by elliotbeken on 2012-07-18
Thanks for the reply, i have PRTG and i am monitoring my server/routers with no problem. I just cant monitor the traffic on the eth0 interface but it is connected just not measuring the traffic.

---

