---
title: "OpenVPN Connects but does not route"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by Herzchell on 2010-09-11
Hi,

First of all I'd like to thank the community for all the help I've been given before. I am a total newb when it comes to Iptables, firewalls and basically anything that has to do with Networking in linux, the case scenario is this: I need to connect to my work's VPN, I can do this fairly easy with OpenVPN GUI in Windows, in Linux though I've gotten to the point where it seems like the network manager connects to the VPN but I cannot ping to anything but my work's server, can't ping google or anything else, I've disabled the firewall "ufw" but I still don't get a connection.

I will be glad to post almost any information you need.

Thank you in advance, I would love to be able to work using Linux instead of Windows.

NOTE: I have browsed several posts regarding this but haven't been able to applying to my case, I'm pretty sure I am missing a step, or that I am not understanding something.

---

### Post by Herzchell on 2010-10-11
123

---

### Post by Drate on 2011-03-05
I ran into the same issue using Maverick Meerkat Desktop edition and the default tools.

The issue ultimately came down to needing to check the "lzo-compression" box in my config because for some reason that option did not import.  Please, if you're still listening, let me know if that solves your issue!

---

### Post by Xinef on 2011-08-01
> **Drate said:**
> I ran into the same issue using Maverick Meerkat Desktop edition and the default tools.

The issue ultimately came down to needing to check the "lzo-compression" box in my config because for some reason that option did not import.  Please, if you're still listening, let me know if that solves your issue!

I don't know about OP, but it sure did solve mine!
Thanks a lot for sharing this, it was a far from trivial guess!

EDIT: for the record and other folks likely facing this issue out there, I'm on Fedora 15, and I had been checking the routing rules (which appear correct) for months...

---

