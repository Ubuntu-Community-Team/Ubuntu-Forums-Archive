---
title: "How can I get apache2 running???"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by mtgmutton on 2009-01-01
I'm trying to set up apache2 so that i can access my files from anywhere with a password... but i'm a bit overwhelmed. I have been googling (which normally works...) and i still can't find a good tutorial for linux. Could anyone help me, or at least guide me in the right direction?

:confused:

---

### Post by Iowan on 2009-01-01
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is only a starting point.  First, set up the server locally.  Then you can work on a no-ip/dydDNS address (unless you already have a static address), and setting up the router (etc) to port forward to your server.

Depending on your needs, it's possible that a VPN or SSH connection may work.

---

### Post by mtgmutton on 2009-01-01
Thanks, this is really helpful :)

But i'm still not sure how to get the folder i want to share into the server...

---

### Post by htmlland on 2009-01-01
You could set the folder as the htdocs if thats all its for or create a virtial link to the folder within the htdocs folder. 

Plus as for securtiy [http://www.apacheweek.com/features/userauth](http://www.apacheweek.com/features/userauth) is a good start.

---

### Post by mtgmutton on 2009-01-01
where is the htdocs folder? I searched my hard drive for it, but I can't seem to find it...

---

### Post by htmlland on 2009-01-01
Did you read through that tutorial priviously posted as that gives advice on securing a directory.. but moving on..

try /var/www/ or look in /etc/apache2/

---

