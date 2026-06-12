---
title: "Problem with DNS"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by Albi on 2006-02-23
Hi, whenever I restart my computer it resets my DNS settings to 192.168.1.1, which is incorrect and I have to change them every time before accessing the internet, and causes a huge delay in the clock synchronization part of startup. Is there any way to fix this?

---

### Post by suRoot on 2006-02-23
Are you getting an address via dhcp?  If so, the DHCP server is responsible for setting DNS, unless you've added something to /etc/resolv.conf.  Check either that file, or you DHCP server to make sure it's configured properly.

I think you can also set DNS entries using the network applet in the gnome panel, so you might check there for any errant entries.

---

