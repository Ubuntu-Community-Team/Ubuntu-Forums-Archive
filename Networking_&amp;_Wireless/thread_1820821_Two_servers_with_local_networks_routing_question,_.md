---
title: "Two servers with local networks routing question, please advice. Thank you."
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by stoynev on 2011-08-08
Hello Guys, 

I have some situation for which I need help:


I have 2 servers, 

One of them has 4 (eth0 1 2 3) ethernet cards and each of them is with IPs of different local networks,

The Second server is connected to the first server through the first ethernet card (eth0).

I want the second server to be able to access the local networks from the first server (eth1 2 3).

Thank you for your help in advance.

Have a nice day.

---

### Post by stoynev on 2011-08-09
:confused:

---

### Post by SeijiSensei on 2011-08-09
Check that IP forwarding is enabled on the first server like this:

[http://ubuntuforums.org/showpost.php?p=10566093&postcount=3](http://ubuntuforums.org/showpost.php?p=10566093&postcount=3)

---

### Post by newbie-user on 2011-08-10
You'd also have to set static routes on the second server.

route add -net [192.168.1.0/24] gw [your router's ip]

Of course, change your network to whatever subnet you're using.  To make it permanent, edit /etc/network/interfaces and add

up route add -net [192.168.1.0/24] dev eth0 gw [your router's ip]

Change eth0 to whatever your network interface is.

---

