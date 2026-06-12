---
title: "How to set up ubuntu 9.04 as server host with XP Professional workstation clients."
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Rencipher on 2009-06-24
Hi people. Im very new at using ubuntu and im looking for help setting up ubuntu 9.04 as host on my server with XP Professional workstation clients. Ive set-up several networks with Server 2003 but never with ubuntu. I would appreciate any help anyone could give me. Thanks.

---

### Post by DGortze380 on 2009-06-24
> **Rencipher said:**
> Hi people. Im very new at using ubuntu and im looking for help setting up ubuntu 9.04 as host on my server with XP Professional workstation clients. Ive set-up several networks with Server 2003 but never with ubuntu. I would appreciate any help anyone could give me. Thanks.

Yes it's possible.
Yes we can help. (Search is your friend too ;) )

What would you like the server to do?
Web Server?
File Server?

---

### Post by Rencipher on 2009-06-25
A file server. Basically, there's an institution i'm opening up but we don't have the funds to purchase Windows server '03 (which I've used on several occasions) so I want to run our database and domain from a samba Ubuntu 9.04 Server with XP Pro clients. Problem is that I'm 100% green at ubuntu.

---

### Post by DGortze380 on 2009-06-26
> **Rencipher said:**
> A file server. Basically, there's an institution i'm opening up but we don't have the funds to purchase Windows server '03 (which I've used on several occasions) so I want to run our database and domain from a samba Ubuntu 9.04 Server with XP Pro clients. Problem is that I'm 100% green at ubuntu.

You've answered your own question.
Install Ubuntu Server
Install and configure SAMBA

There are a number of tutorials available, a quick google search yields dozens of results.

Post back with any specific issues you run into.

---

### Post by superprash2003 on 2009-06-27
well for database you could use mysql , there is a LAMP package available..google that.. for file sharing as mentioned samba would work.. here's a guide on making ubuntu a domain controller [http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

---

