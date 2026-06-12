---
title: "Using Remmina"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by piratestyle on 2011-12-15
Hello all, hoping that you can help me solve an issue using Remmina.
 My friend and I are trying to use Remmina to connect to each others computers via the internet. Most of what I have found online pertains to connecting to computers on the same network. we live 60+ miles away from one another and would like to use the remote desktop to allow us to work on some game compatibility issues. wondering if someone would take some time to explain how to use remmina ( or another program ) to connect our computers and allow remote access. we are both using Ubuntu 11.10. Any takers? 

 Thanks, 
 Pirate Style

---

### Post by Derek Karpinski on 2011-12-16
Do both of you have port 5900 open in your firewall and/or router?

---

### Post by piratestyle on 2011-12-17
Let me look into that. does it have to be that exact port number ?

---

### Post by Derek Karpinski on 2011-12-17
That is the default port.  Unless you've changed things, it should be port 5900.

Take care though. VNC, and remote desktop is highly insecure.  Many here would suggest VNC through an SSH tunnel to be secure.  I have no idea on how to do that.  I just use Teamviewer.

---

### Post by Deuce1912 on 2011-12-17
I personally like to use teamviewer for this. You can login to a computer and control it remotely. Just download the appropriate version of teamviewer from [http://teamviewer.com](http://teamviewer.com) and install it on both computers. It is very simple to use and is also compatible with windows as well for those of your friends who choose to use that OS. 

- Deuce

---

