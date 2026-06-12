---
title: "Emergency traffic stop button?"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by camper365 on 2009-09-06
I am using firestarter (I like it better than ufw. it gives you control over outgoing traffic and has a better interface) and I would like to use it to completely stop any traffic at all. I know how to lock the firewall, and that prevents any new connections from being made, but if there is already a connection, it is allowed to continue. I saw on ZoneAlarm that there was a STOP button that immediately stopped any and all traffic, including connections that were already made. Is there a way to get a button like that?

---

### Post by tgalati4 on 2009-09-06
Install a switch on the power wire of the router.

If that's too drastic, then depending on conditions you can always run a script:

emergency_shutdown.sh

---------------------

#!/bin/sh
# Super cheesy script to shut down network traffic
# run with root privileges
ifconfig eth0 down
wall This network is shutting down!

---

### Post by camper365 on 2009-09-07
Is it also possible to break a connection via the firewall (or not via the firewall)?

---

