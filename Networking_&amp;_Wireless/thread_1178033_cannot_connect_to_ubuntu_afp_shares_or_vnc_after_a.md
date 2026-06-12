---
title: "cannot connect to ubuntu afp shares or vnc after a few hours"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2009-06-04
I have been posting a lot of threads recently. I am really trying to learn all I can about Linux.

I have a new networking problem. I have netatalk vinagre and avahi configured for sharing with OS 10.5.6. When I start Ubuntu all is fine for a time (maybe 3 hours or so) then I can't connect to Ubuntu any more. If I try to connect from OS X it just hangs. It is not an avahi-daemon issue because "sudo /etc/init.d/avahi-daemon restart" does not fix it and I get the same issue if I try to connect manually (Go --> Connect to Server.. type afp://hostname). Also restarting netatalk does not seem to work. Even if netatalk and avahi were fried I should still be able to connect to VNC is I go to Go --> Connect to Server.. and type vnc://hostname, right? but I can't something is amiss and I need to know what it is.

any help would be appreciated.

edit: sorry, I just discovered that the problem is with OS X not Ubuntu (I think). I found that after my MacBook goes to sleep (or I close the lid) then the symptoms occur. Restarting the MacBook completely (not just the Finder app) then allows me to connect to afp or vnc on Ubuntu. What could cause this? I don't want to restat mac Macs whenever I need to get to Ubuntu. Thanks.

---

