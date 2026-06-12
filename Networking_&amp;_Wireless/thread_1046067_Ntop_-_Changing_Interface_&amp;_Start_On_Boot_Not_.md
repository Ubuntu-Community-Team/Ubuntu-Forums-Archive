---
title: "Ntop - Changing Interface &amp; Start On Boot Not Working"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by spikoley on 2009-01-21
I install Ntop on Ibex and I cannot get it to switch interfaces or start on boot.  The config file /var/lib/ntop/init.cfg is set to the right interface.  It is suppose to default to start on boot, but it is not.  Any ideas?  Thanks.

---

### Post by spikoley on 2009-04-25
I have this same issue with Jaunty.  Ntop does not start at boot or use the correct interface.  Any ideas?

---

### Post by grndamgt4 on 2010-02-18
mine does not start at boot either, though it manually starts and runs on the correct interface. I'm wondering if it's because the NIC hasn't come up yet. Will keep searching.

---

### Post by spikoley on 2010-03-27
It looks like a bug with Jaunty.  Karmic does not have this issue.  This issue is solved by upgrading to Karmic.

---

