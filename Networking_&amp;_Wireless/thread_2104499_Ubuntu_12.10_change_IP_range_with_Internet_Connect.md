---
title: "Ubuntu 12.10 change IP range with Internet Connection Sharing"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by viktorsmari on 2013-01-13
How can you change what IP addresses Ubuntu 12.10 distributes using Internet connection sharing?

I'm using the GUI internet connection sharing which works fine but I need to alter the settings.

My router distributes 10.0.1.1-25
My ubuntu machine  has two ethernet cards and eth1 receives 10.0.1.9 from the router.
It shares the connection to eth0 which automatically distributes 10.42.0.*

My second computer then receives 10.42.0.2 and it can access the Internet but cannot access any other computer on the LAN except for the ubuntu sharing machine.

So I would like to change the range from 10.42.0.* to 10.0.1.40-45

---

