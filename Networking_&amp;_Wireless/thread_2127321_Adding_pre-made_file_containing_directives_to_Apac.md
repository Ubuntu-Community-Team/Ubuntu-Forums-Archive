---
title: "Adding pre-made file containing directives to Apache config files"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by BudworthTDog on 2013-03-19
I'm not new to Linux but I am new to Apache. I'm trying to get NoMachine Server Manager to run on my Apache server. For those of you who don't know NoMachine is a remote desktop program. The Server Manger is an internet browser interface to manage the program. Here is how the instruction reads.

> [B]3.2. Configuring your Web Server to Run NoMachine Server Manager
[/B]The BaseDirectory/NX/etc/manager.inc file contains the directives for the web server required to run
the application. This file should be included in the web server configuration file.

Edit the configuration file of your web server and add the following directive for example before the
"Global Environment" section and replace BaseDirectory with the proper path :

Include "BaseDirectory/NX/etc/manager.inc"




Let it be known that I am ASSUMING by server that I need to run Apache. If I am on the wrong track there please let me know.

While that is a direct quote from the manual the actual file-name is manager.conf   
The pathname for the file is /usr/NX/etc/manager.conf

I have the Apache server up and running with the "it works!" message. This includes having the dynamic dns service set up and custom url. I've been trying for the life of me to figure out exactly what they mean by this "Global Environment  and so on. I have books and have been reading all the #notes in the config files but I am just plane stuck. Any help would be awesome.

---

### Post by ahallubuntu on 2013-03-19
~

---

