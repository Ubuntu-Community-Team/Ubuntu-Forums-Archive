---
title: "Ubuntu 10.04 Wireless works for two users but not the third"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by Upkeep on 2010-06-20
Hello,

I'm running Ubuntu 10.04 on an old-ish Lenovo 3000 N100 laptop.  Everything is fine apart from wireless access.  Access is fine from the first two user accounts created on the system, but 3 people share this laptop.  Wireless just doesn't seem to work from the third account.

At boot up, logging in to the third account is OK but the desktop is a little slow to appear.  The network manager applet is present and the local routers show up.  When I try to connect to my router and enter the WPA2 password (not PSK) network manager just hangs.

I tried connecting using Wicd, but that was no better - telling me I was using a bad password (which was not true).  I gather Wicd and WPA2 aren't best of friends from what I've read on the web.

Has anyone else seen this kind of thing?

The third account is for my 8 year old son and it's not selling Ubuntu to him - he wants Windows back!  Help me rescue him before it's too late!

Cheers!

---

### Post by eigenein on 2010-06-21
Is wlan connection in network manager marked as `Available to all users`?

---

### Post by Upkeep on 2010-06-29
Hi eigenein,
 
I have it solved now - I did have the available to all users checked from my admin account, but also had "can connect to wireless networks" checked in my son's.  His account was getting in a mess trying to connect twice to the same wireless network I think.
 
If I can get "Avatar - Legends of the Arena" working for him in Wine he'll be a happy boy.

---

