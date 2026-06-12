---
title: "proxy with additional router help"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by acewildgal on 2009-01-27
Hi there,

I've been a user of ubuntu installed by a programmer/friend for a couple of years now. This programmer/friend of  mine re-built our network system from scratch with two ubuntu pcs running as proxy and file server. These two share files and internet to several PCs running on WinXP.

This is a simple diagram of our network setup, as how I understand it from a non-techie's POV:

DSL Provider
|
|
Modem
|
|
Proxy Server --------------------------File Server
(running on ubuntu)                    (running on ubuntu)
(Shares internet, and files
 from File server to other pcs)
    |
    |
   HUB
    |
=========
|   |   |
|   |   |
|   |   |
XP  XP  XP
PC1 PC2 PC3


Now I need to install a linksys WRT54G broadband router so another XP PC (in another location) as well as a few laptops can connect to the file server as well as the internet via wired and wireless. The very same friend was able to do it for me before but I have no clue how he did it. This friend of mine now lives in another country and has no way of fixing or setting this up for me again :(

I've reset the linksys and have no idea how to make it work simply as a router. The proxy server which is in charge of assigning ip addresses to all PCs in the network has an ip of 192.168.0.2. The linksys has a set ip (set in /etc/hosts) as 192.168.0.11. If I connect a pc to the linksys then the linksys to the hub it looks like it has a connection alright but no file sharing or internet. How do I start with this?

Sorry Im barely knowledgeable how to set it up, if someone can point me in the right places where I need to set the linksys up so it can "talk" to the proxy I would really appreciate it. Thanks.

---

### Post by veloce on 2009-02-10
> **acewildgal said:**
> Hi there,

I've been a user of ubuntu installed by a programmer/friend for a couple of years now. This programmer/friend of  mine re-built our network system from scratch with two ubuntu pcs running as proxy and file server. These two share files and internet to several PCs running on WinXP.

This is a simple diagram of our network setup, as how I understand it from a non-techie's POV:

DSL Provider
|
|
Modem
|
|
Proxy Server --------------------------File Server
(running on ubuntu)                    (running on ubuntu)
(Shares internet, and files
 from File server to other pcs)
    |
    |
   HUB
    |
=========
|   |   |
|   |   |
|   |   |
XP  XP  XP
PC1 PC2 PC3


Now I need to install a linksys WRT54G broadband router so another XP PC (in another location) as well as a few laptops can connect to the file server as well as the internet via wired and wireless. The very same friend was able to do it for me before but I have no clue how he did it. This friend of mine now lives in another country and has no way of fixing or setting this up for me again :(

I've reset the linksys and have no idea how to make it work simply as a router. The proxy server which is in charge of assigning ip addresses to all PCs in the network has an ip of 192.168.0.2. The linksys has a set ip (set in /etc/hosts) as 192.168.0.11. If I connect a pc to the linksys then the linksys to the hub it looks like it has a connection alright but no file sharing or internet. How do I start with this?

Sorry Im barely knowledgeable how to set it up, if someone can point me in the right places where I need to set the linksys up so it can "talk" to the proxy I would really appreciate it. Thanks.

Given the dearth of response, this may be too hard to do remotely.  

Connecting the wireless router to the hub is the easiest approach.  When you say it "looks like it has a connection" how are you assessing that?  Does it have an IP address?  I imagine that the wireless router should be providing IP addresses to the wireless clients these are likely to be on a different subnet to your main network. 

From a wireless client:
Can you ping the router?
Can you ping the proxy server?
Can you ping the file server?

Can you log in to the web interface on the wireless router?  (You are best to do that from one of the wired computers.  )

---

