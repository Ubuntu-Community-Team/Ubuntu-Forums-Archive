---
title: "Help to create an ssh tunnel"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by chimi_12 on 2011-08-03
I wanted to create an ssh tunnel but I do not know what commands to run .. my environment is as follows:

 LAN           Internet          Office LAN
Home PC <-> Linux firewall <->  http server.. 

According to the above what I figure is that I have an internal web server at my job and I need to create a tunnel to access the web server from my PC in my home ... I know I can do a port forwarding with the firewall but I don't want to publish this web server to Internet.. my home PC and both servers (firewall and web) are ubuntu.. my idea is create a ssh tunnel that forward port 8080 on localhost in my home pc, to the firewall (obviously with public ip), and the the firewall forward to port 80 on office web server at my job.. Note that the firewall accepts ssh connections to port 22, same for web server... 

Some idea? I will appreciate any help..

Thanks

---

### Post by gordintoronto on 2011-08-03
Google is your friend.

[http://inside.mines.edu/~gmurray/HowTo/sshNotes.html](http://inside.mines.edu/~gmurray/HowTo/sshNotes.html)

---

### Post by chimi_12 on 2011-08-04
@ gordintoronto hey &#8203;&#8203;thanks for the link, it was really useful!!!

---

