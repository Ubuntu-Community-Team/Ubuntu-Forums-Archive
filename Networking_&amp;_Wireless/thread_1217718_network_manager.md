---
title: "network manager"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2009-07-19
Does anyone know if the gnome-network manager is yet able to handle manual connections?  I am running Hardy and have two NICS.  It is working with the two NICS now so I want to be very careful with the latest release.  I would like to use it but want to make sure that the network manager works better with more than one NIC.  Has anyone had success?

---

### Post by quikone8 on 2009-07-28
bump

---

### Post by cariboo on 2009-07-28
Network Manager should let you set up static ip addresses for both nics. Double-click the network-manager icon, select the device to want to change, then click the Edit button, click the IPv4 tab and select manual from the method drop down. You can then fill in the rest of the details for the device.

---

### Post by quikone8 on 2009-08-25
Has this issue been fixed, I have tried this option before, if there is a power loss the current manager would revert to dynamic and the server would loose static connectivity.  Has this been fixed?

---

### Post by quikone8 on 2009-09-02
bump

---

### Post by Iowan on 2009-09-02
As far as I know, Network Manager can handle more than one interface... it just won't manage more than one at a time.  My laptop works with either wired or wireless, but I haven't even tried to make both work at the same time.  It can be done, but usually involves setting up one interface via */etc/network/interfaces*.

---

### Post by quikone8 on 2009-09-09
The problem used to be that even if the NM was set up for static ip, if the server went down for any reason it would revert to dynamic and therefore loose connection.  Any ideas if this has been fixed?

---

