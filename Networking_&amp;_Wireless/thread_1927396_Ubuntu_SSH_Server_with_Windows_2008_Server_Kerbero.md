---
title: "Ubuntu SSH Server with Windows 2008 Server Kerberos Authentication"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by theamazingbeat on 2012-02-17
hey guys,
So I have a Ubuntu 11.10 machine with openssh. It is on the same network as a Windows 2008 Server (domain controller). What I want to be able to do, is configure the ubuntu machine to accept kerberos authentication from the Windows 2008 server, instead of using for example an SSH key or Password. I have read several articles, but I just need someone to explain it to me in more detail. I have figured how to go into sshd_config and set KerberosAuthentication to yes, but i basically need to know how to route the windows server to the ubuntu box so it knows which kerberos to authenticate with.

---

