---
title: "SMB needs password"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by jason13 on 2013-08-18
I just installed the smb client on two 12.04 computers so i can share them over the home network.
I changed all the sharing options on the folders I want to share, the folders on the laptop show up under "networks" on the desktop in nautilus, but not the other way around. and it asks me for username, domain, and password. and it doesn't accept any of them. I checked my permissions again, and nothing seems to work.

---

### Post by TheFu on 2013-08-19
Got static IPs?
Got firewalls running?
Did you set the passwords using smbpasswd or connect authentication into PAM?

---

