---
title: "I need a central authentication server for linux that is like active directory"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by mmiscool on 2009-09-04
Hello,
I come from the windows active directory world. I am not a Microsoft hater. I don't like there pattens and lawyers who are always mucking up the software industry.
I need to have a server set up for central authentication of users similar to a domain.
I have liked at samba but have found a complete lack of gui configuration tools. That is the one thing that always pisses me off about linux besides the case sensitive file system. I need to be able to configure things in a way that makes my life easy and minimizes the amount of headaches of reimplementing it in the future in diforent environments.

Are there any tools like this that will allow me to configure the equivalent of a active directory domain in linux easy and configure it from a gui for user management, initial set up and so on. Also if it is compatible with a domain like samba and can hook up to windows clients it will be great because it will make my life easy as far as transitioning user to the linux world.

-Mike

---

### Post by bear24rw on 2009-09-04
for configuring samba graphically you can check out gadmin-samba

$ sudo aptitude install samba gadmin-samba 
$ sudo gadmin-samba

dont know about AD though sorry

EDIT:

Looking through gadmin-samba i see a ton of refrences to active directory so hopefully this will help you make the transition

---

### Post by jamesrfla on 2009-09-05
OpenLDAP might be the answer to your active directory question.

---

