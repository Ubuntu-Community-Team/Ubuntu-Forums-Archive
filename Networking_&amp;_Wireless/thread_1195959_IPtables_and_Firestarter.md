---
title: "IPtables and Firestarter"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-06-24
So my firestarter policies are very minimal and I want to uninstall it and make the changes to the IPtable via the terminal.  I'm going for as few apps at startup as possible.  Anyone ever done this?  any thoughts?

Thank You,
Barrie

---

### Post by milton1 on 2009-06-24
Should be very do-able. There are lots of tutorials on iptables if you need them. Just google 'iptables tutorial'. You can also go with the slightly more user friendly ufw system, but this is also just s front-end for iptables.

---

### Post by Barriehie on 2009-06-24
Thank you milton1,  after perusing my table I've only got 3 ports to allow access to, should be a piece of cake!

Barrie

Worked like a charm!  Now I've got squid managing the proxy and my automagic blacklist, boot time is faster and opera is really moving...

---

