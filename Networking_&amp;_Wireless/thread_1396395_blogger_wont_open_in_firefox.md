---
title: "blogger wont open in firefox"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by richlyn9 on 2010-02-02
This is a unusual situation that i am having.
[http://(anything).blogspot.com/](http://(anything).blogspot.com/) wont open in firefox
error: sever not found

i am on a mobile gprs connection using my phone as modem and in 9.10...
i tried using the same connection in windows and the site opened in IE

---

### Post by richlyn9 on 2010-02-03
i pinged [www.rxezlqu.blogspot.com](www.rxezlqu.blogspot.com)  but it could not  and i tried pinging its IP which did ping
however its not just a particular blog that dosent op up but any blog


i also checked for open ports 
richlyn@richlyn-lucid:~$ netstat -anp --tcp --udp | grep LISTEN
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN   

any ideas what the matter might be?

---

### Post by lisati on 2010-02-03
The link you gave opens for me. Are you able to open [http://www.blogger.com](http://www.blogger.com) ?

---

### Post by richlyn9 on 2010-02-05
yes i am able to open [www.blogger.com](www.blogger.com)

---

