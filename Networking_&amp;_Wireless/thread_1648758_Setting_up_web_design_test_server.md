---
title: "Setting up web design test server"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by winfire on 2010-12-19
Hello all,
 
This is my first post, and I am new to the linux community. I am a web developer, but I do not know much at all when it comes to setting up hardware--servers, switches, etc.
 
I have a 1701HG 2Wire wireless router that I use for my home network. I have an old pentium 3 tower that is just laying around, and I want to be able to host my projects on it for testing. Basically, I just want to be able to do everything on my laptop and then upload it to the server for testing.
 
I have set up an Ubuntu LAMP server on the desktop and am able to do everything I want via SFTP; however, I want to be able to type in "projectx.local" in a browser on my laptop to go to one test site, "projectz.local" to go to another, etc.
 
Is this possible, since I do not have the server set up as my gateway? It is merely connected to the router like everything else.
 
Thanks in advance!

---

### Post by CharlesA on 2010-12-19
You'd need to set up VirtualHosts in Apache2 and mess with either a local DNS record or the /etc/hosts file to point projectx or projectz to the IP address of the server.

See here: [http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

---

### Post by winfire on 2010-12-19
Thank you! I chose to go with editing the hosts file.

---

