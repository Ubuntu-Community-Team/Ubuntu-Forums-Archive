---
title: "So, how do I password-protect my wireless internet?"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by Nybb on 2009-03-11
So, a family member recently bought us our first wireless router. I connected it and it seems to mostly just work. Both the main PC and my laptop connect and work fine. I just want to know how to put a password on the connection so others can't just use it?

The router came with a CD with a tool that supposedly does this sort of thing, but of course everything is designed for Windows. Running it in Wine seems to make the program work, but it can't detect the router from inside Wine and therefore can't actually do anything. 

I've poked around the internet a bit but I can only find guides that are about setting up servers and FAQs about connection/network card issues and other stuff that doesn't apply.


Oh yeah, in case it somehow matters, the router is a D-Link DIR-628, and I am running Ubuntu 8.04 (although the only thing stopping me from upgrading is laziness, so if there is some feature in 8.10 that fixes this, that is viable).

---

### Post by Jlb181 on 2009-03-11
In your browser type [http://192.168.0.1](http://192.168.0.1) this will will bring you to the log in screen for your router.  You should be able to just click login until you set an admin password.  Look around in there, change things, it is pretty straight forward.  And don't worry, if something goes wrong, using the reset button on the back of the router resets the factory defaults so you can try again.

---

### Post by lisati on 2009-03-11
Many routers have aweb-based interface which can be used to set passwords. My D-link ADSL modem 
(currently in semi retirement) used 10.1.1.1
as the address.
EDIT: I notice jlb181 has beaten me to a reply.....my comments adjusted accordingly

---

### Post by abn91c on 2009-03-11
the router should have some kind of "online" setup, for instance linksys routers is [http://192.168.1.1](http://192.168.1.1), change your password there, most routers have **admin** as default, also use WPA or higher passkey to your network

---

### Post by mcla0203 on 2009-03-11
> **Jlb181 said:**
> In your browswer type [http://192.168.0.1](http://192.168.0.1) this

If this doesn't work... another common address for the router's page is [http://192.168.1.1](http://192.168.1.1) so try putting that in the URL as well.  Also be sure that you are **wired** to the router and its not a wireless connection.

Once you get into the router configuration page, look for security.  There are different encryptions you can use, a strong one is WPA Personal.  Then you just put a password for it on the config page and apply the changes, then when you connect to the wireless, you'll have to enter this password.

---

### Post by Nybb on 2009-03-12
Wow, thanks for all the quick replies. [http://192.168.0.1](http://192.168.0.1) was exactly what I was looking for and it's all working now. Cheers.

---

