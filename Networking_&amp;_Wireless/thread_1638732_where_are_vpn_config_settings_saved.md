---
title: "where are vpn config settings saved?"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by strider3700 on 2010-12-06
I used to have an ubuntu 10.04 machine with a VPN configured on it.  I've mounted that hard drive and can walk through the entire system but I'm not sure where the configuration for that VPN was saved.  I'm wanting to read it to recreate it on this new machine.  Can anyone tell me where I should be looking?  It has to be saved somewhere...

---

### Post by dineshs on 2010-12-06
If you were using NM it should be in /etc/NetworkManager
or /etc/NetworkManager/system-connections.I havent used VPN so not sure

---

### Post by strider3700 on 2010-12-06
Yep I was using network manager.

The links you gave me points me to where the service is fired from but not where the individual users settings are saved.   I would assume the individual connection setups are saved in the users home directory since they aren't shared with everyone?

---

