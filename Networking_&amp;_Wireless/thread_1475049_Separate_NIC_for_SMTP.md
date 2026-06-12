---
title: "Separate NIC for SMTP?"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by CodPair on 2010-05-06
I have a server with 2 NICs and I have 2 isps. I am currently using a Verizon Fios connection with a dynamic IP to host a website, I have dyndns working to keep the DNS servers updated. The problem with this setup is that all major email providers don't accept email from dynamic IP addresses. To solve this, I have a 768K dsl connection from cavalier with a static IP address plugged into eth0. My problem is that I cant have both interfaces up at the same time.

The other interface would only be for sending smtp.

Does anyone know how to have both ethernet interfaces up at once? Whenever I "ifup eth[x] --force", eth[x] goes up, but the other one goes down.

---

