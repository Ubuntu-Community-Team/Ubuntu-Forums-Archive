---
title: "Forward 2 Internet Connection"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by AnakTeka on 2012-12-30
First sorry for misunderstand about Title. I can't describe it well.

My problems are, I have two internet connections ppp0 and eth0.
I use terminal alot for wget and sync some android repo.
What I want all connection from terminal forward to ppp0 and the rest connection go to eth0.

Anyone can help ? 
Thanks

---

### Post by AnakTeka on 2012-12-30
Anyone ?

---

### Post by Kirk Schnable on 2012-12-30
In order to do what you're describing, you would probably need to have a proxy server running on the other side of ppp0, and a program on your computer which supports a proxy server.  Terminal will not have this type of support as far as I am aware.

Perhaps, if you could explain your goals, and more about your setup, we could propose a better solution.

What is ppp0 and eth0?  Is ppp0 a VPN connection, dialup connection, cellular connection, etc?  I assume eth0 is a local area network with an Internet connection available...

---

