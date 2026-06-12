---
title: "VPN from ZERO"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by sebasg91 on 2010-08-10
Hey guys,

I've seen many posts about setting up VPN's but my doubt goes further.

I just need access to the local network of my office from a Windows XP (which of course is outside the LAN).

I would like this PC to have access to the whole LAN, but what I really need is it to access to an Ubuntu Server (e.g. 192.168.0.10)

The router is a Netgear DG834, which has a built in VPN functionality. So, is it enough if I set it up?

Do I need to install any VPN server in Ubuntu? What if I want to access to another computer in the LAN?

Where should I start? I would really appreciate if anyone can help me with a quick and easy solution.

Cheers,
Sebastian

---

### Post by Iowan on 2010-08-10
One of the first things to check/setup (if you haven't already) will be port-forwarding.

---

### Post by sebasg91 on 2010-08-10
> **Iowan said:**
> One of the first things to check/setup (if you haven't already) will be port-forwarding.

Sorry, do you mean like redirect the access to the router to a particular internal IP? Actually I am doing that with a SSH server.

By the way, I have a fix IP address with my internet connection.

Is it what you are talking about? What would be next?

Many thanks,
Sebastian

---

### Post by Iowan on 2010-08-10
Yup, that's what I meant... You can't access the inside IP address (192.168.X.X) from outside the network. The fixed IP address solves the problem of needing a dyndns.com or no-ip.com account. 

VPN server is still on my To-Do list, so you're ahead of me here...
Good Luck!

A couple of places to check:
[https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN")
[https://help.ubuntu.com/10.04/serverguide/C/index.html]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

---

### Post by sebasg91 on 2010-08-10
Okay, thank you.

If I find something interesting, I'll post it here!

---

