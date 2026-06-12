---
title: "Server Locks me out after reboot"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by aronwalker on 2013-07-20
Hi everyone

This Morning I restarted my server via SSH.
When I Tried to reconnect via SSH, got a message that the connection was refused.
At this point I tested to see if my server was working. It displayed a static web page from Apache (the It works! one). However, Drupal7, owncloud and redmine displayed not available pages in chrome.
I ended up having to go down to the server and physically reset it - This solved the problem. However, i don't know what caused it.
How do i stop it from doing this again.
I will post any logs if you want me to

Thanks

Aaron

Ubuntu server 13.04 64 bit
8GB memory
Intel core 2 duo

---

### Post by 2F4U on 2013-07-20
Since it is probably a headless server, the only thing that helps in further diagnosing the problem is to look into the log files. If, for example, a service doesn't start, you should find further information in the log files.

---

