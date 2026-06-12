---
title: "disabling LAN deliberately"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by levis lover on 2009-11-10
can we disable LAn in ubuntu 9.10 deliberately ? so that no one can use it when a person plugs in the LAN wire?

---

### Post by t0mppa on 2009-11-10
How permanently are you looking to disable it? There are a number of tricks you can do, but if the other users have sudo access, they can bring it back up, if they know what they are doing.

---

### Post by levis lover on 2009-11-11
no other users have sudo access and nobody knws much ..
how can we do it ?
are there any commands to this kind of stuff?

---

### Post by SlugSlug on 2009-11-11
sudo /etc/init.d/networking stop
and to get it back 
sudo /etc/init.d/networking start    

or reboot

---

