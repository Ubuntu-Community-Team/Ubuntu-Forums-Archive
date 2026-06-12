---
title: "resolv.conf / setting nameservers"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by vayu on 2006-06-01
I just installed dapper from the RC and it didn't ask anything about my network or nameservers the way Breezy did.

On Breezy I had set my nameservers in the installer.  They showed up in resolv.conf, but they are no longer there since I also use the machine with DHCP in coffee shops.  But it still works when I'm on my static ethernet network at home.

Man on resolv.conf says it shouldn't be needed and the file on Breezy says do not edit by hand.

But that's what I had to do to get my internet working on Dapper.  Could anyone please explain resolv.conf and why man says it shouldn't be needed?

---

### Post by jvl on 2006-06-21
DHCP usually rewrites resolv.conf after it receives DHCPOFFER, unless you disable it. So that's why you shouldn't edit it. 

There's an option to the dhcp client, so it doesn't update resolv.conf. Search the forums.

HTH

---

