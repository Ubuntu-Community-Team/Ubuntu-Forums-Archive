---
title: "mppe"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by Narusegawa on 2010-01-25
I'm trying to connect with a VPN to my office, I don't get much other than a simple failed to connect with the gui. So I tried the pptp-setup command line.

 ```
FATAL: Error inserting ppp_mppe (/lib/modules/2.6.31-17-generic/kernel/drivers/net/ppp_mppe.ko): Operation not permitted
/usr/sbin/pptpsetup: couldn't find MPPE support in kernel.
```Was my result. How can I fix this? I believe MPPE is required by the office's MS VPN server.

Thanks

EDIT: Nevermind, it doesn't do that if I run it as sudo.

Just won't authenticate for me though

---

