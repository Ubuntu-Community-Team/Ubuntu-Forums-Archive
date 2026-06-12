---
title: "Keepalived + Ubuntu + access from Windows"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by goldengs on 2009-06-12
Hello All,

I've got a problem and it is so frustrating given how close I appear to be closing this project.

Basically I have set up keepalived with a virtual IP 192.168.0.160 and it points to 3 real servers on port 8080. Everything works good, take out one of the real servers, all the notifications get sent, server is taken out of the group and when readded - it comes back.

Checking whilist on the Ubuntu box I can see the server operations functioning as per usual. All is well.

My problem is if I try to access the virtual IP from another windows box or another ubuntu box it will not recognise the services on 192.168.0.160, how do I make it work?

I can ping the VIP 192.168.0.160 from windows and other ubuntu boxes. However, can not connect to the port 8080.

Interesting when I run netstat to check what is listening on port 8080, there is nothing listening at all on port 8080. 

1) Does keepalived only work on the box? 
2) Do I need to install a proxy or something to allow outside connections or something?

What am I missing?

Thanks for any pointers given!!
Kenneth

---

