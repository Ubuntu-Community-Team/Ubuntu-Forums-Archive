---
title: "Mikrotik &amp; Ubuntu :::&gt; plz reply"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by i_hated_microsoft on 2009-05-10
hi again 
this is my second post .. nobody reply me last one 
i'll describe my problem clearly 

1- i just set up Ubuntu 9.04 ( last version )
2- My network managed by **[COLOR="DarkOrange"]Mikrotik[/COLOR]** server 
-- i'm the one only have Ubuntu in all network - all use windows 
3- To connect to the internet i must login to server ( when i open browser automatically login page appear that happen in VISTA 
4- but in UBUNTU ... > when i open firefox i see the title " login page "  for just a second and then connect faild 
5- the problem is not in ubuntu system 
6- the problem is theres some configuration on mikrotik to allow this ubuntu to access 
7- the administrator of Mikrotik is someone who dont know anything about mikrotik server he just refer to some books to set up it .. hes idiot 
he say  "evrything ok the problem in linux system ".. sure dats not right 
nothing changed ... i even disabled my firewall .. 
and port 80 opened .. theres ping replying ... but always connect faild on browser
**[COLOR="Lime"]Any one have ubuntu clint on mikrotik servet ?[/COLOR]**

anyone can tell me whats wrong ????
what ? what ? what ? IS WRONG ?
plz reply i'm in real trouble

---

### Post by msayed2004 on 2009-05-10
Have no idea about it too but my network is also managed by Mikrotik and I am the only GNU/Linux user in it, I have no problems with it except when they turn off sharing, when they do my Ubuntu can't get the IP (and gateway & blah.. blah.. blah.. ) automatically so I have to set it up manually.

So please try to setup your connection manually also try a different browser and try to clear its cache

Good luck :D

---

### Post by i_hated_microsoft on 2009-05-14
i tried all these .. but how to clear cash ?

---

### Post by vidasov on 2011-02-23
Very old post but I saw similar case while trying to connect ubuntu/firefox via hot-spot Mikrotik router, and I didn't see custom login page.
What seams to be that ubuntu/firefox tries to resolve hotspot.local but never manage to. Firefox address bar looks something like:
[http://hotspot.local%23bla..blawww.google.com](http://hotspot.local%23bla..blawww.google.com) if trying to go to google. DNS some domain requests work. Ping of another client works, but my firefox never managed to go outside. MS IE on another machines worked and I heard that might be that MAC/SAFARI doesn't. Have you ever managed to find solution for your problem?

I also have zenmap scan report in attachment.

---

