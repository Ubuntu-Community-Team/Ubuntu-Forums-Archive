---
title: "netcat gives error"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by imgr8 on 2011-02-01
I was trying to make the ubuntu server installation a pxe server following this tutorial [https://help.ubuntu.com/community/AutomatedNodeDeployment](https://help.ubuntu.com/community/AutomatedNodeDeployment) 

In the getMACs script, the netcat command gives the usage error as:

```
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-P proxy_username] [-p source_port]
          [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_protocol]
          [-x proxy_address[:port]] [hostname] [port[s]]
```

I tried different variations of it, if I type:
```
netcat 127.0.0.1 1111
```
then I don't get any error, but
```
netcat -l -p 1111 
```
throws the above mentioned usage error. How can I fix that?

---

