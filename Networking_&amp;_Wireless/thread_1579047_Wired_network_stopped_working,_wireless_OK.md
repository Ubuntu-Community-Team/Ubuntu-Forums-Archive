---
title: "Wired network stopped working, wireless OK"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by michalsiu on 2010-09-21
I'm new to the forum, so would like to say hello first!

I'm not a total newbie, but run into some strange problems with my installation of Lucid.
Everything was working fine yesterday. I shut down the laptop and powered it up this morning and had problems with network:
I have two NICs (wired and wireless). Both are set to pick up IP settings from DHCP and both do, however when using wired network I can't communicate with outside world - can't even ping the default gateway (but pinging 127.0.0.1 or IP address of the NIC no problem, so stack should be OK).
When on the wireless network everything works fine (otherwise I would struggle to write this post :p).
What is very weird though is that I have a VMWare Player installed and using Windows VM on wired network works just great!

I noticed that when you're persistent it happens that you can ping but huge chunks of traffic are lost (e.g. packet 1-10 would pass, 11-40 would be lost, 41-59 would pass and so on).

I restarted Ubuntu, tried shutting down interfaces, disabling networking and nothing helped. I don't recall performing any changes (at least that I would be aware of).
Can anyone suggest something?

BTW. This is not DNS issue as both IP addresses and FQDNs do not work.
When I refer to using a given network (wired or wireless) the other one is down with ifconfig command...

---

### Post by Iowan on 2010-09-21
Are the interfaces in the same subnet? Is there a gateway for each (**route -n**)? Either of the above might cause a problem.

---

