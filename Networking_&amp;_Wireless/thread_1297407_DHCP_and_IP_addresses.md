---
title: "DHCP and IP addresses"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by chemjeff on 2009-10-21
Hello,
Is there a way to configure Ubuntu to tell DHCP to request a specific IP address when it issues its call?

---

### Post by Iowan on 2009-10-21
Check **man dhclient.conf**... Seems like I remember the question in another thread - but don't remember the answer.  If you have access to the DHCP server - and if it's capable - it isn't too hard to set up a static lease based on MAC address. End result is the same - the machine always gets the same IP addrss.

---

