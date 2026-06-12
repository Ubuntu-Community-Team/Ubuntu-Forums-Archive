---
title: "log on to my brothers computer from my house!!"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by styven on 2009-02-28
Hi there,

I want to be able to log in to my brothers computer from my house.
I have searched the forum and have read about ssh and vnc.

I can log into pc on my home network, but want to be able to administer my brothers for him without having to drive 10 miles each time he is struggling.

Both machines are ubuntu behind routers.

Have seen "go to my pc", it is that sort of thing i want to be able to do and it looks like they support linux, but they charge.

Any ideas?

Steve.

---

### Post by Iowan on 2009-02-28
Sounds like SSH/VPN and VNC should work.  You'll need to set up HIS router to port-forward to his machine.

---

### Post by btmartin on 2009-02-28
Yo,

The way I do it is to use dynamic dns to point to the target router.  (some sites offer this for free ex. DynDNS.org).  Then as my fellow Midwesterner says get his router to forward the ssh port from the router to the computer(default is port 22).  And then run an ssh server on his computer.  

The one thing I'd recommend doing before you open up this port to the world is browsing through the security part of the forums.  There are plenty of easy steps described there to secure your server, as it will likely immediately meet some potential intruders.

cheers

---

### Post by styven on 2009-03-01
Thanks for your advice so far guys...

Next time I go round I will look into the port forwarding and go from there.

Steve.

---

