---
title: "Email IP"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by topher83 on 2009-04-26
Hi

I have a program set up where i enter my ext ip and port from work and i can set my computer to dl stuff, 
However as my ext ip is always changing i have to find my ext ip manually and email it to myself manually to pick up at work.

I am looking for a program which will email my ext ip to an email address every time i turn my pc on

Anyone know of anything

---

### Post by kidders on 2009-04-27
Hi there,

The easiest option might be just to run something like **wget -qO- [http://whatismyip.org/](http://whatismyip.org/) | sendmail [email]me@wherever.com[/email]** every now and then. I suppose you could have your box mail you immediately after your network interface comes up and every few hours after that.

---

