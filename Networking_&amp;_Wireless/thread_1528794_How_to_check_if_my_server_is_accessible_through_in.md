---
title: "How to check if my server is accessible through internet on a certain port?"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by ZnoteOT on 2010-07-11
Hello. 

I have a Ubuntu Server box which has the ports assigned 7300 - 7399.

I have set up ssh with port 7399 in /etc/ssh/sshd_config
and then rebooted the computer.

I can access it through 7399 on my local network(Using the local IP for the server), however, it does not work on the outside.(Using the global IP)

I have portforwarded 7300 - 7399 TCP and UDP to the linux IP on my router. 

Any ideas? My portforwarding is working fine on 2 windows computers I have set up. 

Is there any extra configurations I have to do on the Linux box to enable my routers portforwarding or something?

This is how it looks now:
[IMG]http://i32.tinypic.com/317fo93.png[/IMG]

I am using the program "Putty" to connect over ssh both on my local network and outside.

**Nevermind, my router was being gay and didnt save the portforwarded settings. Sorry for this thread!**

---

