---
title: "can't set ip to static"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2009-01-10
I want to use ssh and rsync from my laptop to my desktop for setting up cron backups. To do this on ubuntu I had set both machines up and the router with static IP adds. 

A short while ago I upgraded to 8.10 and decided to try kde. Now I find that the desktop machine has been reset to a dynamic ip, which obviously constantly changes. I cannot find any way to set it back to a static address in the kde desktop and menu's. Network manager simply shows me a blank box, apparantly I don't have a connection, even though I obviously do. 

In gnome this was easy, on kde it seems weird. 

Can anyone help please

---

### Post by geus on 2009-01-10
Just google for (k)ubuntu and static ip.
see: [http://www.linuxquestions.org/questions/ubuntu-63/setting-a-static-ip-in-kubuntu-8.10....-690093/](http://www.linuxquestions.org/questions/ubuntu-63/setting-a-static-ip-in-kubuntu-8.10....-690093/) for example

---

### Post by Iowan on 2009-01-11
I usually edit /etc/network/interfaces directly... The link **geus** provided seems to go into detail.

---

