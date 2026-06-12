---
title: "Cannot access url of local server via vpn but can connect via ssh"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by oxxlswordfish on 2013-02-23
Hello, I am new to Ubuntu and networking in general. I am currently having problems accessing the url of the local webserver at work via vpn. The server at work is running a Debian 6 squeeze with apache2, PHP 5.4, mysql and java.

Currently i can connect to the server via ssh or sftp but not http. When trying to connect to the server via telnet it shows 
Trying 192.168.0.**...
Connected to 192.168.0.**.
Escape character is '^]'.
GET /
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://phpmyadmin.webserver.local">here</a>.</p>
<hr>
<address>Apache/2.2.16 (Debian) Server at phpmyadmin.webserver.local Port 80</address>
</body></html>
Connection closed by foreign host.

I am not sure what to change or do in order to fix it so i can access the url via vpn.

---

