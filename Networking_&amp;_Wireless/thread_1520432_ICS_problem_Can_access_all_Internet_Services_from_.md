---
title: "ICS problem: Can access all Internet Services from client?!"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Blacklightbulb on 2010-06-29
I just connected my main fedora 13 box with an Ubuntu 9.10 client. Everything is working fine except I can't access anything other than Google from the Ubuntu client. Youtube and wiki take forever to load?! I can ping the other sites just fine though?!

apt-get doesn't work either?!

Can anyone hint me the cause of the problem?

EDIT:

I disabled the firewall completely to check if the firewall was at fault but the problem persists?!

---

### Post by Iowan on 2010-06-29
[Here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") is a help page in slow IPv4/IPv6. [This]("http://ubuntuforums.org/showthread.php?t=1376506") thread discusses (or links to discussion) about checking MTU values.

---

### Post by Blacklightbulb on 2010-06-30
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") is a help page in slow IPv4/IPv6. [This]("http://ubuntuforums.org/showthread.php?t=1376506") thread discusses (or links to discussion) about checking MTU values.



Thanks for the reply!

Thanks to you I managed to repair the problem. I tweaked the MTU (from nm-applet) to 1492 a standard for my type of connection.

---

### Post by Iowan on 2010-06-30
Fixed is good!!!
Consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if the problem stays fixed. :)

---

