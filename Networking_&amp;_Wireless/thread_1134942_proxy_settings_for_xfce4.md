---
title: "proxy settings for xfce4"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by cirrusminora on 2009-04-24
I've switched to xfce4 desktop recently but there remains a hitch with the proxy settings. Earlier in Gnome preferences, global proxy configuration could be done (through Network Proxy) but I can't find any such option in xfce4 settings menu. What can I edit/install to get it fixed ? I need to switch between proxy and direct connection ; so having an interface would be nice. I looked around the archives but couldn't find anything. After all, its not that esoteric of stuffs. 


F.Y.I : I'm using Gutsy 7.10 with xfce4 desktop. I've retained the default Gnome stuff though.

---

### Post by ChrisB111 on 2009-12-22
This would be usefully for me to, I am using pure xubuntu and cant install the hardware drivers as it comes up with a proxy error.

Chris

---

### Post by szagabesz on 2010-03-28
Add the following line to /etc/environment :
```
http_proxy="http://user:pwd@proxyaddress:port"
```

I found this solution here: [http://ubuntuforums.org/showthread.php?t=215627]("http://ubuntuforums.org/showthread.php?t=215627")

It works for me, after reboot the machine. It also works with Google Chrome on xfce4!

---

### Post by iwanmr on 2011-05-05
Can be done by running
gnome-network-properties

steps doing it:
Alt F2 <-- run a command
Type gnome-network-properties

Voila :D

---

