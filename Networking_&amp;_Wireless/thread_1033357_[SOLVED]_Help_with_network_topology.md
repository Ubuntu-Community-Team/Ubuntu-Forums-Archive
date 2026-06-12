---
title: "[SOLVED] Help with network topology"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by kslat3r on 2009-01-07
I have the following network: 

[IMG]http://i40.tinypic.com/21amxsn.png[/IMG]

How can I access my VNC server on my Windows PC through my server (which is running Ubuntu 8.04)? The server is the only remote point of entry to the network.

Please bear in mind that I don't currently have physical access to any of the network components (they are in my university house and I won't be there until Sunday). Although I can install software onto the server over SSH, I do not have access to the Windows PC to install anything or make any changes. Ideally, I would like to register my Ubuntu box that is with me at the moment on the network and retrieve an internal IP address.

Does anyone know of any solution to this problem?

Many thanks in advance,

kslat3r

---

### Post by kslat3r on 2009-01-07
I've answered my own question:

Forward port 5900 on router to 192.168.1.3
vncviewer 192.168.1.3 -via [router hostname/IP]

Thread should be marked fixed/closed

---

### Post by superprash2003 on 2009-01-07
please mark this thread as SOLVED under THread Tools..

---

