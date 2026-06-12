---
title: "URL won't resolve from within DMZ"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by abasel on 2009-08-05
Our moodle site resolves fine from within our network, as well as from outside. 

The moodle box is an Ubuntu 8.04 server sitting in our DMZ. Any machine that connects to the DMZ can not resolve to the URL. 

Am I able to set up some sort of host file so that when the URL is entered from within the DMZ, that it points to the moodle box within the DMZ?

And how do I do this?

---

### Post by superprash2003 on 2009-08-05
the hosts file is located at /etc/hosts

---

### Post by abasel on 2009-08-05
Ok, so I now have the following host file

127.0.0.1 localhost
172.16.0.2 elearning.rosmini.school.nz elearning


when I ping elearning.rosmini.school.nz from the DMZ, it should return 172.16.0.2 but it doesn't.

I am obviously doing something wrong.

Once I updated the host file, I ran

/etc/init.d/networking restart

---

