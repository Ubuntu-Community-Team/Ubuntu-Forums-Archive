---
title: "Gsync and Unison have stopped working"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by gdbutcher on 2008-12-02
I'm running Ubuntu 8.10 on both my Desktop, and trusty NX9005 laptop. Laptop connects to internet and desktop through wireless router. 

I installed Gsync and Unison on saturday, they both worked brilliantly for 3 days then have suddenly stopped. I've been using the GUIs for both apps, the error messages are:

**Unison**: Fatal error lost connection with server

**Gsync**: ssh: connect to host 192.***.*.* port 22: No route to host

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(635) [sender=3.0.3]

Whats the problem? and how do I solve it? I'm fairly new to linux. Any help you could give would be much appreciated.

---

### Post by gTinker on 2008-12-03
[QUOTE=gdbutcher]Whats the problem? and how do I solve it? I'm fairly new to linux. Any help you could give would be much appreciated.[/QUOTE]

OK, have a close look at the error messages.

[QUOTE=gdbutcher]
**Unison**: Fatal error lost connection with server

**Gsync**: ssh: connect to host 192.***.*.* port 22: No route to host

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(635) [sender=3.0.3][/QUOTE]

Notice that in both cases it indicates that there is no connection. That is a network problem. You will have to determine what has changed since it was working. Was either system rebooted, upgraded, etc? You can use the tool ping to test the connection by trying to ping from one system to the other by IP address. Verify, the IP address on both machines with sudo ifconfig. Post back with more information about how your network is configured and/or ask any further questions that come up for you. There will be lots of people here to try and help.

---

### Post by gdbutcher on 2008-12-05
Thanks gTinker I've solved my problem now, Your prompts pointed me in the right direction. My router is set to automatically assign IP addresses and for some reason had given my laptop a new one. I did google the error message but the answers seemed to indicate a port issue... so thanks again for your help much appreciated! :D

---

### Post by gTinker on 2008-12-06
I'm glad I was able to help you focus on the issue.

I'd guess that you had that system turned off for a while before the problem occurred and that it was unable to respond for a new lease when the lease from the router was up, thus the router issued a different IP address the next time it asked for an IP address. But that's just a guess.

Most gateway/routers with DHCP servers have the ability to always assign the same IP address to a given MAC address (each ethernet card has a MAC address), thus you can accomplish the same thing as having a static IP address and your routes for grsync and unison will be preserved each time DHCP hands out a lease. It would probably be a good idea to set your system up that way if you aren't going to use static addresses for the two systems that have to be able to talk to each other all the time.

You might choose to mark the thread as solved by editing your original post title.

---

