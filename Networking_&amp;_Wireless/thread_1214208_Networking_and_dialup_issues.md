---
title: "Networking and dialup issues"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Viper187 on 2009-07-15
I'm running Ubuntu 9.04x64 with a serial modem. I had to install the gnome network manager to even use dialup, but I don't know how to kill the original network manager ("Network Connections") or if I need to. Anyway, the real problem here is I can't get it to keep the dialup as its primary connection. The ISP resets the connection every 6 hours and Ubuntu refuses to redial, probably because it sees other network interfaces. Also, anytime I change any network setting, Firefox, and Pidgin both break. Pidgin started showing my LAN address instead of my dialup IP, so I assume Firefox has the same issue. They see the network and refuse to acknowledge the dialup connection anymore. What can I do to ensure the dialup connection remains primary and auto reconnects properly? It's really pissing me off.

Believe me, if there was broadband available here I'd get it. My only option right now is that dish BS, and the only plans I can find are non-negotiable service contracts with obscene limitations on the amount you can download every month.

---

### Post by vrkalak on 2009-07-15
I'm having the same problem, kinda?  I am, also, running Ubuntu 9.04.01

I have Wireless Broadband with one server and have switched to another server.  And my new Broadband won't connect?

Do I have to go in and delete all remnents of the first Wireless Broadband, and re-install the new one?

Also, same as the OP, my dial-up Broadband is acting up, seems to be the same problem as theirs.

---

### Post by Viper187 on 2009-07-17
Well, gnome-ppp knows enough to reconnect when my ISP boots me, but xchat and other programs aren't so smart. It takes them forever to realize they've been disconnected, if they realize it.

---

### Post by vrkalak on 2009-07-29
The actual connection problem was **solved**.  Fix'd with the help I got form the Forum.

My next issue is:  :confused:

When the wireless USB gets disconnected, it won't re-connect automatically.  I changed the Network Manager to do this, and have done everything I can think of to correct this, but I am at a loss.

The only way to get my internet connection back is to re-start the computer . . . then, it connects automatically.  But, doing this is a PITA.  There must be a way?

---

