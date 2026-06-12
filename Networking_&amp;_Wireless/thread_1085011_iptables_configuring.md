---
title: "iptables configuring"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by fissionmailed on 2009-03-02
What I want to do is have it where samba traffic is going through eth2 and everything else is going through eth0. 

I did iptables-save into a file and and added this at the end

```
-A OUTPUT --destination-port port 0:62000 -o eth0 ACCEPT
-A INBOUND --source-port port 0:62000 -i eth0 ACCEPT

-A INBOUND --source-port port 0:139 -i eth2 ACCEPT
-A INBOUND --source-port port 445 -i eth2 ACCEPT
-A OUTPUT --destination-port port 137:139 -o eth2 ACCEPT
-A OUTPUT --destination-port port 445 -o eth2 ACCEPT

```

I read that it reads it from top to bottom so this shouldn't effect anything before it but it'll route the traffic. 

Would this work and if so how to I implement the changes? I'd much rather edit some text files and load them than add each policy in CLI.

---

### Post by fissionmailed on 2009-03-14
Don't worry about it. I don't need the help anymore.

---

