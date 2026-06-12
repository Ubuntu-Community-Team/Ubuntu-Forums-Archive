---
title: "Configuring TINC to access internet sites via the host"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by notessensei on 2009-11-06
I'm often work in environment where internet access is severely limited as in large portions of interesting sites are blocked. I can however access my own servers. So I'm planning to setup TINC as VPN tunnel solution.
How would I configure TINC:
a) allow outgoing connections on the server
b) the client to try  direct connection first and fallback to tinc if that doesn't work
.or.
c) Have a button to switch on/of the tinc tunnel?

---

### Post by CedSha on 2010-01-18
- Hoops it goes wrong  Pls check message under !!!

---

### Post by CedSha on 2010-01-18
Hi,

As your thread is a little old, I am not sure you solve or not your problem. I have been encountered the same problem as I live in one country where the Internet has severe limitation. However I found a very interesting way to solve this by browsing through ssh.
Please check the following link to have further explanation. In most modern machine you'll have nothing to install to do it !
I have Ubuntu 8.04 on my server and 9.10 on my computer.
[>> private-internet-browsing-ssh]("http://www.ubuntuhq.com/content/private-internet-browsing-ssh.")
the most important point is :
```
ssh -D 7070 username@IP-OR-DOMAIN
```
For trying ppurpose you can use root as username.
IP-OR-DOMAIN is the IP of your server.
You then proxy your browser to localhost port 7070 there is plenty of extensions to help you switch the proxy if you use firefox.
If you found another way to do it please post reply, it would be interesting to share about it.
Hope this help :)
CedSha
--
[www.lineaire.net](www.lineaire.net)
[www.excalibur.com.cn](www.excalibur.com.cn)

---

