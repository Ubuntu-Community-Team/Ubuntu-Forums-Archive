---
title: "Net connection prob with 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by ashu365 on 2009-10-31
Net connection prob with 9.10

Using Jaunty was a superb experience. 
I am using Jaunty from last 3 months, browsing net without any errors. 

Then I have installed ubuntu 9.10, 
but **not able to connect "Wired [DSL] connection".**
network manager is not working for me. 
I downloaded fresh 9.10 again, still having prob with network connection. 

My DSL connection is working properly with other OS'. 
I tried installing 9.10 at friends PC also. 
It get installed properly,but we face same prob with net connection.
please help

Thanks in advance
Ashu

---

### Post by Turtle.net on 2009-10-31
could you post the result of ```
lshw -C network
``` ?

---

### Post by paulbyr on 2009-10-31
mine connected with no problem.  I use a home network (ethernet to a Linksys  router).  I am just puzzled because it seems to take a lot longer (than 9.04) to start up and get to the username/password place.  Is that because 9.10 has "tons of new features"?

---

### Post by Turtle.net on 2009-10-31
Aren't you a little bit off topic here ?
For the boot up time are you talking first boot up time or regular one ?
Anyway, you should post in a thread that talk about boot up time and not connectivity.
Or maybe join the discussion on IRC [#ubuntu-classroom ]("http://webchat.freenode.net/?channels=ubuntu-classroom")

---

### Post by skits on 2009-10-31
SOLVED?
I just installed (from bootable cd) 9.10. It went OK. When I tried to run it, I could not use Firefox (page load error) nor access the network. I could not change anything to do with the network - permissions problem.
I found how to change root's password (sudo passwd root   in a terminal window) and enter a new UNIX password for root. Then I logged out and back in as root, intending to investigate further - and lo and behold, I could use Firefox. 
So I logged out and back in as me, and here I am.
I have no idea why this worked or whether it will continue to work!!!!!
The computer (Dell Dimension 8200) is connected by wire to a D-Link 604 router/firewall and then to a DSL modem.
Hope this helps somebody

---

