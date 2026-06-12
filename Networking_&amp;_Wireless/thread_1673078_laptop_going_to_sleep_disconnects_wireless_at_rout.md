---
title: "laptop going to sleep disconnects wireless at router"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by pavemen on 2011-01-21
Running Ubuntu 11.04 on a Gateway LT3103U netbook. 

It's running fine except for that fact that when it goes to sleep (timeout or lid closed) or going into suspend or otherwise restarted/shutdown, my router restarts.

It's a DLink DIR-655 that has been working fine until I changed this netbook to Ubuntu. 

After installing Ubuntu on the netbook, it found my SSID being broadcast and I added the connection by supplying the WPA2 password. I have full network access (local and internet).

It's just the router restarts and all my other machines lose connections. 

The router is using DHCP but supplying IPs based on MAC. Netbook is set to use DHCP.

Any ideas?

---

### Post by mantoe on 2011-01-21
Mine does the same thing...but i thought that was normal:confused:

---

### Post by pavemen on 2011-01-21
why would it be normal for a router to be restarted when a machine connected to it closes it's connection with said router?

when I close the lid on my netbook, my wife's laptop, the PS3, and all other computers here loose connectivity.

---

### Post by pavemen on 2011-02-06
well I found that modem-manager is the culprit. if I stop the process, there is no impact on the rest of the network when i close the netbook lid or shutdown.

now i need to figure out how to not let it startup

---

