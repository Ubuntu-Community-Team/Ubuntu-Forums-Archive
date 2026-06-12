---
title: "ufw and ipv6"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by _generica on 2009-07-16
Hey,

I had a pretty standard, simple ufw config for my server.

Allow some ports (about 3 of them) from everywhere.
Deny some ip addresses (about 20).

I recently enabled ipv6, and found that nothing would work, until I disabled ufw.

Since then, I have tried to get ufw to behave.
I set 'IPV6=yes' in /etc/default/ufw.
I restarted ufw.
I deleted and re-added my 'allow' rules for ssh, apache.

And even though ufw status shows:

22                         ALLOW   Anywhere      
80/tcp                     ALLOW   Anywhere      
25/tcp                     ALLOW   Anywhere      
22                         ALLOW   Anywhere (v6) 
80/tcp                     ALLOW   Anywhere (v6) 
25/tcp                     ALLOW   Anywhere (v6) 

I still get blocked ssh traffic, for instance, and this shows up in my /var/log/messages as though I asked for it to be blocked.

Even ping does not work, although it is enabled in before6.rules

Aside from moving to shorewall or something more complicated, is there any ideas for how to get ufw to work with ipv6?

Ubuntu version is Jaunty.
ufw 0.27-0ubuntu2

cheers,

     / Brett

---

### Post by Thedjatclubrock on 2010-01-03
Same issue [http://ubuntuforums.org/showthread.php?t=1371345](http://ubuntuforums.org/showthread.php?t=1371345) here

---

### Post by _generica on 2010-01-03
Thanks! That seems to have solved it.

---

