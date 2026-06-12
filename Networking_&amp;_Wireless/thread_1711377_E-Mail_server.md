---
title: "E-Mail server"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by szokeptr on 2011-03-21
I have Ubuntu 10.10 server edition on my box on which I set up a blogging service. The main problem is that user have to register and to do this they have to activate their account by a clicking a link in an email, but they are not receiving any EMails from our server and in this I'd like to ask for your help. 
I have a domain, say it mydomain.com 
I have MX record on mail.mydomain.com
I CAN receive email but can't send any. 
I tried Postfix, Sendmail and Exim4 too.

Please help me ASAP! Thank you in advance!

---

### Post by SeijiSensei on 2011-03-21
Does your ISP block outbound port 25 connections?  If so, do they have a server you can use to relay mail?

Quick test.  From your server, run:

```
telnet gmail-smtp-in.l.google.com 25
```

If your connection times out, you're blocked.

---

### Post by szokeptr on 2011-03-21
Isn't Google's SMTP on 465 port? 
Anyways, I tried it here is the result[:(]:```
root@server:~# telnet gmail-smtp-in.1.google.com 25
telnet: could not resolve gmail-smtp-in.1.google.com/25: Name or service not known
root@server:~# telnet gmail-smtp-in.1.google.com 465
telnet: could not resolve gmail-smtp-in.1.google.com/465: Name or service not known
```

My ISP is not providing any mail servers and until today I thought that they are not blocking port 25 but it seems they do. I will look forward, however I would be glad if you could help me to set up the mail server correctly to send mails.

Thanks in advance!

---

### Post by Thund3rstruck on 2011-03-21
> **szokeptr said:**
> My ISP is not providing any mail servers and until today I thought that they are not blocking port 25 but it seems they do. I will look forward, however I would be glad if you could help me to set up the mail server correctly to send mails.

Thanks in advance!

Yea, I think just about every ISP blocks port 25. I was prototyping a product for a customer at home a few years ago when I realized I was being blocked. Luckily, I have an external host for one of my websites who gave me an alternate port to use to get through my ISP's firewall. 

You can use google's gmail as they offer an alternate port also, which I think is 993 or something like that.

---

### Post by szokeptr on 2011-03-21
I'm using GMail now. I dropped a mail to my ISP to ask what's going on but they did not respond yet. The main problem is that GMails server rewrites the From: to the GMail which you used to authenticate. :(

---

