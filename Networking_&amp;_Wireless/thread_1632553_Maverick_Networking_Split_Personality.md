---
title: "Maverick Networking Split Personality"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by TheFr00n on 2010-11-28
Hi gang,

  So, I use Ubuntu 10.10 on an old Dell laptop as the router for the house. It shares its Vodacom 3G with the rest of us, via the network port of the laptop.

  This works fine. We can all surf to our hearts' content.

  I can also VNC into the desktop of the router machine if I ever need to accomplish X, Y or Z on it, which is handy.

  However, I cannot for the life of me SSH in, or connect to the MySQL server that also lives on that machine. This is a pain.

  What I want to do is set up a database on a remote server, and then tunnel in via SSH. I'm trying to test that configuration using local machines on my network. My desktop machine happens to be XP, and I'm using Putty to try to initiate the SSH connection, but I keep getting a message saying NETWORK ERROR: CONNECTION REFUSED.

  I tried connecting directly to the database (OpenOffice lets you plug into a remote MySQL database using a connector), and I got a similar message: error 10061, which is a network connection refused.

  I thought it was somehow firewall related (I've experimented with GUFW), so I reset iptables with -F, but that had no effect whatsoever.

  I'm going nuts - any ideas?

---

### Post by TheFr00n on 2010-11-28
91 views and no love?

C'mon, throw me a bone :(

---

### Post by grahammechanical on 2010-11-29
You have lots more experience in this field than I do, so I would not attempt to teach you, but could it be that the user on the XP machine does not have the same permissions as the user who created the MySQL database files?

Regards.

---

