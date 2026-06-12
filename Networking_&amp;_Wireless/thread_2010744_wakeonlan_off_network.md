---
title: "wakeonlan off network?"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by Mr.Dee on 2012-06-26
I am unable to wakeonlan when I am off network.

Frustrating since I can wake from my cell phone (i guess that is off network) and when I'm on my own network.. but when i'm away and try from the command line, it's no good.

The syntax I am using...
$ wakeonlan -i 12.34.56.789 -p 9 00:00:00:00:00:00

Lots of googling and can't find such a simple thing.

---

### Post by Mr.Dee on 2012-06-27
bumpity bumpity boop

---

### Post by papibe on 2012-06-27
Hi Mr.Dee.

Waking up a computer over the Internet (or from outside your network) requires several things to work. In most cases, it is not possible that easily.

First, your router has to be able to forward broadcast packets. That is not an standard functionality as some of them don't support it.

Then, routers forget hardware addresses very rapidly (arp cache clearing). One way to overcome this would be setting either an DHCP reservation, or static IP (on the router). AFAIK, this should be MAC based.

For example, I've been able to do this in my home network, but working only for a few minutes right after I shutdown the machine. My router uses hostnames to reserve LAN IPs (instead of MAC addresses).

The only permanent solution that I've implemented in the past is having a device inside the network that do the work for you. This could be as obvious as a home server, or as simple as a router with built-in WOL functionality (dd-wrt for example).

Hope that helps.
Regards.

---

### Post by Mr.Dee on 2012-06-27
Thank you Papibe.  Your advice does solidify what I have in mind.  Now that you mention temporary functionality, It doesn't appear to work with my cell phone now.  Will try to setup the static routes on the router.  I'm trying to move away from having anything running at home so a home server is not the direction I'm going.

dd-wrt is also in my future, but not immediate.

One thousand thanks.

---

