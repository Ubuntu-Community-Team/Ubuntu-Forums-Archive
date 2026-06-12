---
title: "Wicd needs administrative privileges"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by skamarla on 2009-12-28
I have recently installed wicd, after a short unsuccessful test of knetworkmanager. Wicd seems to work better, but I have a problem with it: it won't start (and users won't get network access) until the superuser logs on and gives the root password in a window that says "wicd network manager needs administrative privileges".

Part of the wicd setup was to get all the users into the netdev group, and I have double checked this worked.

Shouldn't wicd start the network as part of the regular boot, and not wait for any particular user? I would like users to access the network freely, and move from wired to wireless at will.

Thanks in advance.

---

### Post by skamarla on 2010-01-10
OK, I have finally fixed it. Here's how.

First, there was no problem with administrative privileges at all. The real problem was a corrupted configuration file (/etc/wicd/wired-settings.conf) that prevented wicd from starting normally. Then the client thought that there was a permissions problem, and asked for the password. In fact, that didn't help either.

How to find out what's really going on: check /var/log/wicd/wicd.log. That should give you a good clue. In my case, a line with empty brackets ([]) kept getting added every time I restarted the system.

This second problem went away when I commented out the wlan0 and eth1 definitions in /etc/network/interfaces. In fact, if you check the wicd documentation, it's important to have the interfaces file as clean as possible.

---

