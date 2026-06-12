---
title: "netcat not working in listen mode"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Borisaniya on 2010-02-21
Hello,

I have used the netcat with following command in other versions of Ubuntu but its not working with Ubuntu 9.10

$ nc -l -p 3333
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-P proxy_username] [-p source_port]
      [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_protocol]
      [-x proxy_address[:port]] [hostname] [port[s]]

What is wrong with it ?

Thanks in advance

---

### Post by liam_p on 2010-04-14
Hello,

I'm using lucid and had the same problem.  ncat worked (been renamed?)

---

### Post by Cillean on 2010-05-07
I encountered the same problem. The solution is simple: In the new version, the port is specified without the -p option.
The new syntax would be:
```
nc -l 3333
```

---

