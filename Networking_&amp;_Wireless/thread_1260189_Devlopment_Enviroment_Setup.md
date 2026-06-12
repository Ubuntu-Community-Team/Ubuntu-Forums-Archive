---
title: "Devlopment Enviroment Setup"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by jacqolive on 2009-09-07
Hi All

I have not been working on linux for very long and I am not a network person so even my skills on windows are not that great regarding networks. I hope some one can shed some light on this for me. I have Ubuntu 9.04 installed and I am setting up my development enviroment, Glassfish 2.1 and Mysql(cant remember the version, it is the latest). Glassfish is installed and working as I can reach it on [http://localhost:4848](http://localhost:4848), mysql still needs to be installed as well as virtual box with 2 ubuntu vm's. What I would like to do is resolve my glassfish url"localhost:4848" to a domain name, the same will be the case for mysql as well as the 2 vm's (witch will also have glassfish and mysql). I have tried to edit my /etc/hosts file, I have added "127.0.0.2:4848 test" but this does not work when I go to test in my browser, however when I put "127.0.0.2 test" and go to test:4848 in my browser I do get the correct page. The problem seems to be with the port, I wont mind installing BIND if this is required. So my questions are

1. Would BIND be a good option as I will have my desktop as well as 2 or more VM's, each with app or/and db servers and I dont want to change config files on all the VM's if BIND will allow me to do it on my desktop and just point the VM's to BIND.
2. If BIND it not the right thing how would I resolve a url with port to a domain name.
3. If BIND is the right way to go can some please suggest a good tutorial on setting up this sort of thing in BIND.

---

