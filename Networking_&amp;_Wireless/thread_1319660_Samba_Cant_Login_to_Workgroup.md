---
title: "Samba Cant Login to Workgroup"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by dontgetshocked on 2009-11-08
Hey, I cant login when it asks for password,i.e. the popup box.I click on Places/Network/windows network/workgroup then choose computer and here is where it asks for your password, it already has filled in WORKGROUP and username. I un-installed samba and winbind and re-installed all to no avail.
I am entering the correct password but it still does not work.

Suggestions Please!

---

### Post by Roehrich on 2009-11-19
latest samba clients are broken, see [https://bugzilla.samba.org/show_bug.cgi?id=6880](https://bugzilla.samba.org/show_bug.cgi?id=6880)

had the same problem on mandriva 2009.1_64 after update, downgraded lib64smbclient0 to built 3.3.2

---

### Post by dmizer on 2009-11-19
Many people have been able to solve this problem in Karmic by following the howto located in the 6th link in my sig.

---

