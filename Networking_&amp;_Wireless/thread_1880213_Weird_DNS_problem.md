---
title: "Weird DNS problem"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by Geoff_L on 2011-11-13
I've built a test server to get to grips with phpBB. For info, I'm using phpBB 3.0.9 under Apache 2 on Ubuntu 10.10. The installation is failing to send mail to new test users, who are part of my local domain (i.e. localnet.local). I have a mail server running on my network: mail.localnet.local with IP address 192.168.1.25. I'm using port mapping on my router/firewall to pass incoming SMTP to the mail server. The DNS server for my local network is a Windows 2000 Server machine on 192.168.1.3.

Although phpBB can't resolve mail.localnet.local to 192.168.1.25, nslookup can:
[INDENT][FONT=Fixedsys]$ nslookup mail.localnet.local
Server:  192.168.1.3
Address: 192.168.1.3#53

Name:    mail.localnet.local
Address: 192.168.1.25[/FONT]
[/INDENT]Also, when I enter the IP address for my mail server into phpBB rather than its URI, phpBB has no problem sending the mail. As this is something that might cause a problem with future projects, I'd be grateful for some insight. Can anyone shed some light on why this is happening?

Thanks,

Geoff

---

### Post by SeijiSensei on 2011-11-13
What happens if you add an entry to /etc/hosts for the mail server?

---

### Post by Geoff_L on 2011-11-13
> **SeijiSensei said:**
> What happens if you add an entry to /etc/hosts for the mail server?
Thanks for the reply. To answer your question, phpBB successfully resolves mail.localnet.local to its IP address.

---

