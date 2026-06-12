---
title: "Wireless network settings aren't remembered after reboot"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by ubnewbie2 on 2009-03-11
I have Ubuntu Studio 8.04 installed on a Thinkpad T42.  Everytime I restart it, the wireless network does not connect.  Each time I have to open System>Admin>Network.  I notice it hasn't remembered my saved location.  Even switching to that location does not get it connected, I need to go to the wireless connection properties and retype the password.  Then it connects to my access point.

How can I get it to do this at startup automatically?

---

### Post by ubnewbie2 on 2009-03-12
This has to be a bug.  I removed all settings (renamed the /etc/network/interfaces file) and reconfigured it from scratch.  It puts the same encrypted password string in the new file, but still cannot connect after a reboot until I retype the password.

---

