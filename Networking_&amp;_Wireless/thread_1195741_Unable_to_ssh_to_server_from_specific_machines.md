---
title: "Unable to ssh to server from specific machines"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by jbbarnes on 2009-06-24
Hi,

I am trying to ssh to my Ubuntu 8.04 Server from my Xubuntu 9.04 laptop. When I do, I get the error:

ssh: connect to host servername port 22: Connection refused

However, I can connect just fine from my Windows XP box on the same subnet using Putty. I checked the ssh_config and hosts.allow and hosts.deny on the server, but didn't see any reason one machine would be allowed a connection and the other not.

Can someone tell me what to check next?

---

### Post by prshah on 2009-06-24
> **jbbarnes said:**
> 
ssh: connect to host servername port 22: Connection refused

Can someone tell me what to check next?

Maybe a DNS resolution issue; can you try with the IP address instead of the servername?

Depending on the result, we can decide how to proceed.

---

### Post by jbbarnes on 2009-06-24
> **prshah said:**
> Maybe a DNS resolution issue; can you try with the IP address instead of the servername?

You are absolutely right. It works fine with an IP. Thanks for the reply.

---

### Post by prshah on 2009-06-24
> **jbbarnes said:**
> It works fine with an IP.

If your server has a fixed IP address, you can try adding the details to the /etc/hosts file on each client eg```
xx.xx.xx.xx servername

```

---

