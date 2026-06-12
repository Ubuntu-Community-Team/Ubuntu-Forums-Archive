---
title: "Cannot receive mail on my ubuntu server :("
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by simonrichards150 on 2008-12-31
Hi all, I have a problem with mail on my ubuntu server.

Hopefully someone can help me ;)

I can send emails fine using postfix. I sent an email from my server to my gmail account, but when I tried to reply, the message never arrived at my machine, and gmail didn't give me an error either.

It is really confusing me.

Anyone know what im doing wrong? How can I send emails to my ubuntu machine? :)

---

### Post by simonrichards150 on 2009-01-01
Bump with some more info

I have a domain with an A record pointing to my public IP address.
My router is forwarding ports 80,21,22,25,110,443,5900 to my server.

Sending mail works fine, but I can't send to [email]user@mydomain.co.uk[/email]

Maybe something to do with MX records?

---

### Post by simonrichards150 on 2009-01-01
Thanks for all your help, not. :(

I figured it out in the end. I made MX records on my domain and changed my server's hostname.

Now does anyone know how to set up squirrelmail? :)

EDIT: I worked it out.

---

