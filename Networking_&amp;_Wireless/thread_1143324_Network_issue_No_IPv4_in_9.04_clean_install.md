---
title: "Network issue: No IPv4 in 9.04 clean install"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by blazemiskulin on 2009-04-29
I've spent the past 4 hours trying to find out what's going on with this:

I unboxed a brand new Dell Insprion 530 this afternoon, nuked the Vista that came pre-installed, and installed a clean copy of Kubunty 9.04 right away.

I have one serious issue:  the box won't connect to my network. After a couple hours of trying every possible configuration I could think of (and calling in outside help), we discovered that the NIC isn't showing an IPv4 address--only IPv6.  Since none of my local network hardware is setup for IPv6 (nor, I suspect, is my ISP), I think I've found the problem.

So... How do I get IPv4 functioning?

The only reference I've been able to find is a bug from a few years ago in which a hardware clock setting caused an issue.  I checked that, and my settings are correct.

Anyone able to help with this?

---

### Post by blazemiskulin on 2009-05-02
The problem has been solved.  It turned out to be a DHCP issue with my router.

---

