---
title: "Bind9 configuration problem"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by alchemiss on 2012-01-12
I'm trying to set up dns on a vps with Ubuntu 10.04. Being a complete newbie in netwioking, I followed this guide: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto).
Here are my configuration files:

Thank you for reading this :3 Any help will be greatly appreciated!

---

### Post by Doug S on 2012-01-12
I get the same answers as you. I think you might not acutally be using your DNS for lookups, but rather external DNS servers. I also think your registrar for axisautomotive.org is pointing to dns4.name-services.com (and others) instead of, perhaps, where you want (i.e. ns1.scservers.com (and others)).
 
Sorry for my brief reply, but I am out of time just now. I'll be back in a few hours, but probably someone else will help further.
 
Oh, by the way, welcome to Ubuntu forums.

---

### Post by alchemiss on 2012-01-13
Thank you for reply :) It turned out that among many other mistakes I forgot to set up my nameserver at the hoster. Now everything works!

---

