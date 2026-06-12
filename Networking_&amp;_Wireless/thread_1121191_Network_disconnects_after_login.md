---
title: "Network disconnects after login"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by *4564* on 2009-04-09
Hey guys, I believe this is a common problem having browsed the forums here but I'm hoping someone can still give me a fix, or advice. 

I'm running Ubuntu 8.10 on the latest kernel, and using NetworkManager Applet 0.7.0 to handle my networking on two computers, one accessing my router through WPA2 wireless, the other through a cat5E cable. When I start a session on either of these computers, the networking connects and retrieves an IP address and can access the internet (as proven by pinging [www.google.com](www.google.com)) for all of about 30 seconds. And then the ping stops returning any information, and nothing on the computer can access the internet or even ping the router. The wireless is still connected, and both connections have IP addresses. What's happening here? 

So far, the only way I've found to fix it is to restart the router. If the router is turned on after the session is started, life is good and there are no problems with networking at all. However, since both these computers get heavy use, it's not a decent fix. 

Here's what I've tried so far on my wired computer (though my wireless computer is behaving in the same way): 

First I tried [this]("http://ubuntuforums.org/showthread.php?t=53321"):
```
ifup eth0
ifdown eth0
```
Both of these give errors which I can provide if necessary. 

Then I tried [this]("http://ubuntuforums.org/archive/index.php/t-1101522.html"):```

sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart
```
They did what they were supposed to do but didn't change anything. 

What haven't I tried? Can I provide any additional information to help answer this question? :?:

---

