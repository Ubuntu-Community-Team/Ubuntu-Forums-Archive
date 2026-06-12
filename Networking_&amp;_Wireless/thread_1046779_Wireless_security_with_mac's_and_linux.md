---
title: "Wireless security with mac's and linux"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by rektruax on 2009-01-21
I've set up a nice home network with my 8.10 Ubuntu, 2 Apple Macbooks, 1 Apple Imac, (all Intel Mac's) and a Windoze XP 64.

The Windoze is direct, but the other 4 share a wireless router. They all connect perfectly and strong, but when I went to put a WEP pass phrase in the Linksys WRT54G connection, the Ubuntu box connected fine, but the Mac's all wouldn't recognize the password. Kept telling me it was wrong. It wasn't. Here's the kicker...

The Ubuntu is the newest addition. The Mac's all used to connect fine to WEP using a password. I merely reset the Linsys when I was trying to get the Ubuntu wireless up and running (I didn't want any hassles). But when I finished that, and set the router back up with the same settings and password, the Linux box was the only one that would work.

Assist SVP...

---

### Post by dmizer on 2009-01-21
> **rektruax said:**
> But when I finished that, and set the router back up with the same settings and password, the Linux box was the only one that would work.

Assist SVP...

This looks to be a Mac problem rather than a Linux problem? Can you connect to the router with your Mac if the Ubuntu box is turned off?

---

### Post by rektruax on 2009-01-22
I too thought that. But can't imagine why they connected fine with the WEP password before the Ubuntu was thrown into the mix. It's as if the Linux is prioritizing it's network connection, and recognizing the security protocol as exclusive. Granted, there are a few WEP flavors to choose from (WEP, 128 hex, 128) but the different OS's don't seem to want to share connections with the same setting.

Weird. It's really not a biggy right now. I share the network with my family and a kid in the next apt. They're the only ones I ever see in the network so I guess it's cool so far. But if someone else moves into the building, I'm gonna want to be able to lock my access.

We'll see... Thanks for the response.

---

### Post by bgerlich on 2009-01-22
Strange, BTW you do realize that it takes about a quater of an hour to crack WEP ?

---

### Post by dmizer on 2009-01-22
> **rektruax said:**
> I too thought that. But can't imagine why they connected fine with the WEP password before the Ubuntu was thrown into the mix. It's as if the Linux is prioritizing it's network connection, and recognizing the security protocol as exclusive. Granted, there are a few WEP flavors to choose from [noparse](WEP, 128 hex, 128)[/noparse] but the different OS's don't seem to want to share connections with the same setting.
It's very unlikely that Linux is causing this problem.

Can your Mac connect when the Ubuntu box is turned off? If not, then obviously, Ubuntu is not causing the problem.

Try rebooting your router. Sounds crazy but it works more times than you think. By rebooting, I mean unplug the thing and leave it off for several seconds before plugging it back in.

This is either:
1) a router problem.
-or-
2) a mac problem.

---

### Post by rektruax on 2009-01-22
> **dmizer said:**
> It's very unlikely that Linux is causing this problem.

Can your Mac connect when the Ubuntu box is turned off? If not, then obviously, Ubuntu is not causing the problem.

Try rebooting your router. Sounds crazy but it works more times than you think. By rebooting, I mean unplug the thing and leave it off for several seconds before plugging it back in.

This is either:
1) a router problem.
-or-
2) a mac problem.

I shall try that. Thank you...

---

