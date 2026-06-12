---
title: "netstat shows web server connecting to itself?"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by Gakumerasara on 2011-07-14
Hi; I've been experiencing some home web-server slowdown issues lately, and I wanted to see if it's a problem with the server itself.  I'm not sure if this might be the problem, but upon checking netstat -tn, I see over 15 instances of the following:

Proto Recv-Q Send-Q Local Address           Foreign Address         State 
tcp        0      0 192.168.2.9:59332       xx.xxx.xxx.xxx:80       TIME_WAIT

where 192.168.2.9 is the server's local address, the local address port varies, and the foreign address is the server's web address.  If anyone knows what might be causing this and/or how to fix it, I'd appreciate the help.  Thanks!

---

### Post by jmoorse on 2011-07-15
Use 'sudo netstat -tpn' to see what process is handling the connection, let us know if you have further questions.  Do you have the webpage open on the server itself?

---

