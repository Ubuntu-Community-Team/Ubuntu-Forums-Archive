---
title: "Where does SNMP data go?"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by sutabi on 2010-09-01
My end goal is just to see some sort of data out from a Cisco Router 3662. However I think I have snmp running correctly but I have no idea where the snmp data goes. I am having zero luck on the web.

So I've setup a SNMP demon on my ubuntu box. 
```

rocommunity public
agentaddress localhost:161
```

And then on the router (xxx.xx.xx.xx == ip address to my ubuntu box)
```
snmp-server community public RO
snmp-server enable traps bgp
snmp-server host xxx.xx.xx.xx public
```

So I get some stats from my router:
```
800 SNMP packets input
    0 Bad SNMP version errors
    0 Unknown community name
    0 Illegal operation for community name supplied
    0 Encoding errors
    800 Number of requested variables
    0 Number of altered variables
    0 Get-request PDUs
    800 Get-next PDUs
    0 Set-request PDUs
    0 Input queue packet drops (Maximum queue size 1000)
901 SNMP packets output
    0 Too big errors (Maximum packet size 1500)
    0 No such name errors
    0 Bad values errors
    0 General errors
    800 Response PDUs
    101 Trap PDUs

SNMP logging: enabled
    Logging to xxx.xx.xx.xx.162, 0/10, 101 sent, 0 dropped.

```

So it must be sending it, just where on my ubuntu box is it?

---

