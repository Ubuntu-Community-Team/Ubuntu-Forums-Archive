---
title: "Strange Winbind/Samba problem"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by quetoo on 2011-04-20
Hey guys, I hope someone can give me some kind of direction on this. 

I've got a Win2k3 DC, and then I've got a file server running Ubuntu. Two times a day I have an application server (also Ubuntu server) pushing data to this file server, it's authenticating itself against AD. I've implemented Winbind and Samba 3.3.2 to handle this for me. The issue is that I will get odd WBC_ERR_AUTH_ERR errors and connection resets to the DC at random intervals. So, let's say the first data push in the morning works without issue when the second data push rolls around in the afternoon I'll start getting auth failures. It's almost like a network outage but when I get notification from the application that the push failed there is no network error - also restarting Winbind immediately fixes the issue. So to that end I've got Winbind restarting on the hour; while this fixes the problem it's not a good solution. When it works it works without issue and allows the authentication but once it gets boned up it's dead in the water until a restart. 

Also this only effects my production network, I can't seem to replicate it in test (yet). 

Both systems are Ubuntu server 9.04.

Any thoughts? I'm happy to paste logs or config files or anything else that anyone might like to see. 

Thanks!

---

