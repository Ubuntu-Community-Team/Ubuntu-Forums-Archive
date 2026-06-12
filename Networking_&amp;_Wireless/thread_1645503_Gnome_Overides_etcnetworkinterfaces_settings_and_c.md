---
title: "Gnome Overides /etc/network/interfaces settings and creates IP conflict"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by Rengar on 2010-12-14
Good Afternoon,

I have a static IP setup for eth0 via the /etc/network/interfaces file.
In gnome the same static IP got configured for eth3. 

This is causing an IP conflict that causes the box to not be reachable from my remote location once Ubuntu desktop (gnome) has started.

Is there any way to change this configuration without having to boot into Gnome itself to do it? 

The IP address for eth0 cannot be changed as this is required to have the server reachable at all.

Thanks

James

---

### Post by Rengar on 2010-12-14
I was able to fix the issue, by removing the ~/.gconf/system/networking directory.

---

