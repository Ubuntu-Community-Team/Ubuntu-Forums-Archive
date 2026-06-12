---
title: "Port 1000 access denied webmin"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by Rikoos on 2011-08-26
Hi, After a few days of reading, searching and consulting friends i haven't found the solution yet :(

Last week i installed a frsh 10.04 Ubuntu server which i want to use as file/print server. Installation went fine and the server is running fine. I'm able to connect thru ssh but i want to use webmin to admin the server remote.

When starting webmin locally on the server it works fine but when i want to connect on my laptop (same network) with https://<ipserver>:1000 i get a message access denied??

I'm not a unix/linux expert so i don't know what to do now :(

Does anybody knows what to do now? A link to a site will do fine to solve this. (ANY HELP IS WELCOME!!)

thank you

---

### Post by SlugSlug on 2011-08-26
at a guess I would say the webmin config is set to only allow access from localhost

---

### Post by Rikoos on 2011-08-26
thnx, but when checking on the server it says allowing all connections.

Or is there a special place to check this?

---

### Post by SlugSlug on 2011-08-26
I'd  check the configs in /etc/webmin  if it exsists -- i've not installed it

---

### Post by e79 on 2011-08-26
> **Rikoos said:**
> When starting webmin locally on the server it works fine but when i want to connect on my laptop (same network) with https://<ipserver>:1000 i get a message access denied??

Unless you changed the login port manually, it is not 1000 but 10000 (ten thousand)

[B]https://<ipserver>:10000

[/B]Hope this helps

---

### Post by Rikoos on 2011-08-27
OMG !!!! :lolflag: i'm ready for THE wall of shame.  

You are right, it's 10000 instead of 1000!

Where is the coffee;-)

Thnx

---

### Post by e79 on 2011-08-27
I'm glad I could be of some help :P

Cheers

---

