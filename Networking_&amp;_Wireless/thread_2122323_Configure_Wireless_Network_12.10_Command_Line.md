---
title: "Configure Wireless Network 12.10 Command Line"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by pfig88 on 2013-03-04
Okay, so I've recently set up a server with Ubuntu Server 12.10 to run as a headless server.  When I ran the OS installer/setup it gave me an option to immediately connect to a wireless network (this box has a wireless card), and so I connected to my home network.  Since then I've turned the server on/off multiple times and it's always automatically connected to the wireless network until yesterday.  Usually I would SSH into the server, but yesterday I couldn't, so I hooked a keyboard and a monitor back up and learned that it wasn't connected to the wireless network.  Yesterday and today I attempted countless efforts to reconnect to the network from the command line based on advice from threads I found on google, but have been unsuccessful.  This is extremely frustrating: surely it shouldn't be this difficult?  I'm tired of trying to edit my interfaces file.  Many of the threads I've found seem to date back quite a while.  Can anyone please help out?

---

### Post by pfig88 on 2013-03-04
85 views and zero replies?  Does anybody have any ideas?

---

### Post by steeldriver on 2013-03-04
well you're not really giving any information - what wireless device do you have? how is your network configured (static? DHCP?) is the interface coming up at all (ifconfig)? what is your current /etc/network/interfaces file?

---

### Post by pfig88 on 2013-03-06
Here's my current interfaces file [http://pastebin.ubuntu.com/5592183/](http://pastebin.ubuntu.com/5592183/)
The interface does come up in ifconfig, and when I scan, I do find the wireless network I'm trying to connect to.

---

