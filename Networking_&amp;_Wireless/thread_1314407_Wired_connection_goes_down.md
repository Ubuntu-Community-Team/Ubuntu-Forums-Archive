---
title: "Wired connection goes down"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by shizakapayou on 2009-11-04
I have an Ubuntu 8.04.3 desktop that a few of my users SSH to for some big runs.  I use Zenoss SNMP to keep an eye on this machine, as well as my servers.  This desktop has a habit of losing its network connection several times a day - I'll get an alert from Zenoss that the machine is unavailable, and 5 minutes later when Zenoss checks again, the system is available again.  I've confirmed that the machine is in fact off the network by trying to ping it, and by trying to SSH to it when I get an alert.  Uptime shows it has been up for days, so it's not rebooting spontaneously.  The only thing I've been able to find in logs is from syslog:

```
Nov  4 12:05:33 lids1 lsassd[5908]: 0xb0df7b90:Error code -1 occurred during attempt 0 of a ldap search. Retrying.
Nov  4 12:05:33 lids1 lsassd[5908]: 0xb0df7b90:Clearing ldap DC connection list for domain 'EXAMPLE.COM' due to a network error.
```

This machine is joined to an Active Directory domain using Likewise, thus the above events.

The machine itself is a Dell Optiplex 760 with a PCI-Express Intel Pro/1000 GT added in.  Are there any logs I could check with more specific information?  Anyone have any clues?

---

