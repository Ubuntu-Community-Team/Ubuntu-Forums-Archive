---
title: "OpenVPN connectiont reset"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by T3kG33k on 2012-01-07
I'm seeing a strange issue on my Maverick laptop that I can't seem to reproduce on my other Maverick laptop.  Weird, I know.

What I can't put my finger on is could it be the the router or the laptop or both?

I just reset the router to factory defaults with a 30-30-30 reset and reconfigured the bare essentials and left the firewall at it's default settings (only configured the wireless and login password).

Here's what's happeneing.  I can connect and authenticate and my internet connection is being routed to my home network and I can access the internet for a short period.  I I'll ping google or a host on my home network but only about 30-50 requests are sent until I lose all ability to route packets to that network.

I've repeated this scenario time and time again and now I'm asking for some help.  Here's the error and conenction log

---

### Post by T3kG33k on 2012-01-07
Figured out the issue.

Apparently you can't connect from the 192.168.1.0/24 subnet to a 192.168.1.0/24 subnet.  I made this simple change to my home network and the issue appears to be resolved.

---

