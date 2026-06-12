---
title: "Problem with Apache when using for trac"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by sainathas on 2009-05-12
I have installed trac on my ubuntu 8.10. For that I installed apache2,apache2.2-commonm,apache2-mpm-prefork. I configured apache fro ssl.
When i tried to start apache /etc/init.d/apache2,it says 
------
 * Starting web server apache2                                                                                                                               (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
------

So i thought some other process is using port 80. When I checked it is nothing but /usr/sbin/apache2. It was installed with apache2-mpm-prefork.

Why this /usr/sbin/apache2 is starting during startup of machine?
To run /etc/init.d/apache2 I need to kill the /usr/sbin/apche2.
Can anyone plz tell me how to solve this so that I can run apache and trac without problems.

---

