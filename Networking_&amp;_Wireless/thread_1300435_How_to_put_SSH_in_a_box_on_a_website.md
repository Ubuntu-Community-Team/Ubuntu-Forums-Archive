---
title: "How to put SSH in a box on a website"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by blazemore on 2009-10-25
I've got a web server running, and I'd like to be able to ssh into it from anywhere. SSH works, and the web server works at [http://rory.is-a-geek.com](http://rory.is-a-geek.com)

I want to have a terminal come up on that page, with a login prompt, so I can administer my server from a web browser. Is that even possible?

Alternatively, does anyone know of any decent frontends I can install, similar to amahi (I never had much luck with that one though)

---

### Post by Lars Noodén on 2009-10-25
You can access your machine like this, assuming your login name is 'blazemore'

ssh -l blazemore rory.is-a-geek.com


It is a good idea to find your way around the shell first before setting up webmin.  If the web server is down, then so is webmin and you need shell access to fix it. 

What kind of administrative tasks do you want to do with the server?

If you are just looking to copy files, then filezilla does sftp quite well.

---

### Post by blazemore on 2009-10-25
No, you misunderstand. In a box on the website, I want a terminal, where I can ssh into the server (and then into any of the machines on my LAN) from a web browser. Anywhere.

---

### Post by Lars Noodén on 2009-10-25
There are some java applets here, one or more might work:
 [http://linuxmafia.com/ssh/java.html](http://linuxmafia.com/ssh/java.html)

You'll have to test.

---

