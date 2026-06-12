---
title: "Printer sharing"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by 73ckn797 on 2013-06-05
Ubuntu 13.04

I find no option to share a printer over local home network. Hp-lip and Samba are installed. No option in System Settings under printers either. I have been able to do it in prior versions.

---

### Post by 73ckn797 on 2013-06-07
Any suggestions?

---

### Post by tgalati4 on 2013-06-07
Printer sharing is usually turned on by default.  Try opening [http://localhost:631/printers](http://localhost:631/printers)  This this page is not found, then perhaps *cupsd* is not running.  You might need an update to fix a bug which interferes with *cupsd* from starting.

---

### Post by 73ckn797 on 2013-06-08
cupsd is running.

---

### Post by pqwoerituytrueiwoq on 2013-06-08
I am using xubuntu 13.04, it was easy to find
Menu-> settings manager -> printers -> Settings (in the server menu)
you can do it from here also
[http://localhost:631/admin](http://localhost:631/admin)

---

### Post by critin on 2013-06-08
I assume you checked "Server" Settings on the page opened from System  "Printer'.  I don't run 13.04 so may be in another location.

---

### Post by 73ckn797 on 2013-06-10
> **pqwoerituytrueiwoq said:**
> I am using xubuntu 13.04, it was easy to find
Menu-> settings manager -> printers -> Settings (in the server menu)
you can do it from here also
[http://localhost:631/admin](http://localhost:631/admin)

I went into the admin server settings and set printer for sharing the other day but since then my modem failed and I have been distracted from following up with it. New modem installed by cable company today.

---

