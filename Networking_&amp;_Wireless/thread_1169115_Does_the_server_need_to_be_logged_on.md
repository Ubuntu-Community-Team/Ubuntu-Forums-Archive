---
title: "Does the server need to be logged on?"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by randyklein99 on 2009-05-24
I have successfully (:D) setup a samba server on an old laptop.  I was just wondering if you actually had to log in before those services take effect?  Or are does the samba service start once its booted and at the login screen?

---

### Post by squaregoldfish on 2009-05-25
You don't have to log in - the SAMBA server will be started on boot.

Steve.

---

### Post by Iowan on 2009-05-25
You can probably configure it otherwise, but services *should* start at bootup.  My DHCP/Samba server runs headless - login is via SSH.

---

