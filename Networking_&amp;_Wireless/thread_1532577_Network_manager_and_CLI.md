---
title: "Network manager and CLI"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by A_M_S on 2010-07-16
Hello.


Anybody know if its safe to reconfigure some network parameters (IP, DHCP, DNS...) using the CLI with network manager running?


Tnx.

---

### Post by Iowan on 2010-07-16
I'm not really sure, but I've edited some of the files Network Manager uses. If you edit configuration file for **dhclient**, the new values  would be used on the restart/reboot. Other changes (like static IP?) might get overwritten on next restart/reboot.

---

### Post by capscrew on 2010-07-16
> **Iowan said:**
> I'm not really sure, but I've edited some of the files Network Manager uses. If you edit configuration file for [B]/B], the new values  would be used on the restart/reboot. Other changes (like static IP?) might get overwritten on next restart/reboot.

That would make perfect sense.  NM will overwrite anything you put in the /etc/network/interfaces and /etc/resolv.conf files on reboot.

As NM also calls dhclient (but doesn't overwrite it) all changes made there will be used on reboot.

---

### Post by A_M_S on 2010-07-16
Tnx for the replies.

Anybody know if the same problem occur with WICD?

---

