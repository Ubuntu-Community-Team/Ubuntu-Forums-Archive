---
title: "traffic monitor per user (like BSD IPF uid rules)"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by bobdoll on 2009-03-30
Hi,

I'm looking for a way to monitor the IP traffic form a local unix user (running an application).

I used to do it on freebsd with the following rules in ipfw and parse the counters:
ipfw -q add 1500 pass all from any to any uid UNIXUSER in via xl0
ipfw -q add 1510 pass all from any to any uid UNIXUSER out via xl0

I can't find a way to do it with iptables or any other means on linux ?
Do you guys have a clue on how i could do it.

just in case you asked, this user runs a daemon and multiple scripts. It listens on one port but connects to many clients on a variety of ports. So it's a nightmare to create rules to capture it's traffic. That's why i used the user level on BSD (which, sadly I'm not running on this server).

Thx

---

