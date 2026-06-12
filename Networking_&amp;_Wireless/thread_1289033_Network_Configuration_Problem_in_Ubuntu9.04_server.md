---
title: "Network Configuration Problem in Ubuntu9.04 server"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by ana11 on 2009-10-12
Hi:

I have installed Ubuntu 9.04 server. And at the time of installation i have given** proxy serve**r setting.
After installation i have install ubuntu GUI desktop.

But by using Network Manager, i am unable to set new network setting.It will keep blank or it does not create new connection.

Actually i want to install Proxy Server on this machine now.
I am thinking that , i am getting this problem because of the proxy setting which i have declared at installation time.


So can any body tell me the solution for that?


Thank You.

---

### Post by ana11 on 2009-10-12
Hi:

I have installed Ubuntu 9.04 server. And at the time of installation i have given** proxy serve**r setting.
After installation i have install ubuntu GUI desktop.

But by using Network Manager, i am unable to set new network setting.It will keep blank or it does not create new connection.

Actually i want to install Proxy Server on this machine now.
I am thinking that , i am getting this problem because of the proxy setting which i have declared at installation time.


So can any body tell me the solution for that?


Thank You.

---

### Post by Dejai on 2009-10-12
Alright I am going to assume this is the squid proxy server and I am also going to assume that being a proxy server you have an ethernet connection. Can you please report the status of ping 192.168.1.1 and ping [www.google.com](www.google.com) also could you share the ifconfig details. If you are connected to the internet on eth0 which shouldn't require the gnome network manager then onto the matter of getting your proxy up. 

[http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/](http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/)

---

### Post by ana11 on 2009-10-12
Hi:

Actually before installing Ubuntu server, my proxy server is on another Ubuntu Desktop machine.
And at the time of installation of Ubuntu Server i have given the ip of that Proxy Server in Proxy server setting.

And now after installing the new Ubuntu Server, i have installed new Squid proxy server on that machine.

But it  shows the error message that Proxy Server Refused Connection.
And cross mark is there on Network Manager icon.


Can any body help me?

Thank You.

---

### Post by cariboo on 2009-10-12
Please don't double post on the same subject, I have merged your two threads.

---

