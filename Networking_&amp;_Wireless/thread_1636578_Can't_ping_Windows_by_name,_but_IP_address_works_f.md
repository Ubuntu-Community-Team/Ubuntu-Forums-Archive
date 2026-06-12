---
title: "Can't ping Windows by name, but IP address works fine."
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by damateem on 2010-12-03
My Windows machine can ping Ubuntu by name, but Ubuntu can only ping the Windows machine by using it's IP address.

This was working fine in both directions until I purged Samba. After purging Samba, I couldn't ping in either direction unless I used the IP address. I did some reading and found that Samba provides NetBIOS functionality that allows the machines to resolve host names without a DNS. Since I'm not running a local DNS, I decided to reinstall Samba. Unfortunately, I've not been able to restore it to full working condition.

I don't want to use hosts files as all the IP addresses are assigned automatically by DHCP.

I want to be able to access the Windows machine by name.

What can I do to figure out where the problem lies and, ultimately, fix it?

Thanks

---

Sorry, I accidentally posted the same message twice. Please ignore this one and respond to the other.

---

