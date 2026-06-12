---
title: "SSH tunelling to surf the Internet, and use Steam"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by :-( on 2009-11-29
At my high school, you can only connect to the internet on one port, port 80. This means that I can't use Steam during lunch, or connect to m mail without using a browser, or anything. I'm curious: Is there a way to tell my computer to send all of my information from Steam and Evolution through port 80? For give my lack of technical knowledge, I'm still learning about computers and networks and stuff.

---

### Post by :-( on 2009-11-29
Bump.

---

### Post by kevdog on 2009-11-30
I don't understand your question.  Port 80 is the remote port.  Does your high school filter packets that only have a destination port on port 80?  What is steam?

---

### Post by R0peE on 2009-11-30
SSH tunnel is not the best option for you. Try running a VPN server at home, and set it to listen on port 80, and you can redirect all youre internet traffic to it (i suggest openvpn, because its easy to configure on server side, and client side to) and you can reach your home network from it, it's quite a good thing imho :)

---

### Post by ktrnka on 2009-11-30
Like R0peE said, VPN is probably your best solution due to having to forward every port used through ssh. However, you can tunnel ssh over http with a program called corkscrew.

 It appears that there are a few other ways to accomplish this as well:

[http://www.mtu.net/~engstrom/ssh-proxy.php]("http://www.mtu.net/~engstrom/ssh-proxy.php")

[http://dag.wieers.com/howto/ssh-http-tunneling/]("http://dag.wieers.com/howto/ssh-http-tunneling/")

[http://wiki.kartbuilding.net/index.php/Corkscrew_-_ssh_over_https]("http://wiki.kartbuilding.net/index.php/Corkscrew_-_ssh_over_https")

[http://www.ubuntugeek.com/how-to-use-ssh-via-http-proxy-using-corkscrew-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-use-ssh-via-http-proxy-using-corkscrew-in-ubuntu.html")

Knock yourself out.

---

