---
title: "ssh connections made on port 443"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-10-15
I've been reading about making an ssh connection through a firewall on port 443 (the https port).

Two questions:
1, is it possible to distinguish between an ssl connection made by a web browser on port 443 and a ssh connection made on the same port?

2, would setting up an ssh connection to exit a firewall on port 443 interfere with a web browser having made or trying to make a https connection through the firewall on the same port?

---

### Post by Ceiber Boy on 2011-10-15
> **Ceiber Boy said:**
> I've been reading about making an ssh connection through a firewall on port 443 (the https port).

Two questions:
1, is it possible to distinguish between an ssl connection made by a web browser on port 443 and a ssh connection made on the same port?

2, would setting up an ssh connection to exit a firewall on port 443 interfere with a web browser having made or trying to make a https connection through the firewall on the same port?

I've been able to answer question number 2 as no, having an active SSH connection on port 443 dose not interfere with a web browser also using the same port. If anyone could explain why i would be interested to know!

I tested this by installing two Ubuntu OS in virtual box and was able to connect to the second (server) with SSH on port 443 and still was able to access HTTPS websites in Firefox (client).

---

