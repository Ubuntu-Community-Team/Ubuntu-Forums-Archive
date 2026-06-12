---
title: "Nautilus Samba share error"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by sciff90 on 2009-04-23
When trying to view my network shares from within the network link in the places menu I get an error saying:

"Failed to retrieve share list from server" 

However when I enter the computer's IP address in the nautilus address bar I can still connect to the other computers. This seems strange to me and it only just started.

Any thoughts would be greatly appreciated

---

### Post by conorturton on 2009-04-23
It's to do with a bug in gvfs-smb authentication that's been there ever since Ubuntu 8.04 and nobody knows how to fix it. Basically it happened when Gnome changed from 2.22 to 2.24 and changed to using gvfs for everything. You'll find that using other desktops such as KDE, the problem doesn't exist.

---

### Post by swerdna on 2009-04-26
Is there another File Manager (like Konqueror) that can be installed in Ubuntu, to use instead of nautilus for Network Browsing?

---

