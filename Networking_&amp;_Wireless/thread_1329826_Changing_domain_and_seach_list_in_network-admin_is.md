---
title: "Changing domain and seach list in network-admin is overwritten"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by PorterHouse_01 on 2009-11-17
IN 9.04 I'm trying to change the 'domain' and the 'search domain' list using the network-admin utility.

I expected the change to only take effect on reboot (...yes I realise that if I knew the syntax I could restart the inet daemon without rebooting but I'm a bit rusty in that regard having spent too long and too much money on m$crap)

I thought at first the problem might be my ser perm's and so I added myself to the root group and that change persists after a reboot.

But the changes to resolv.conf made by network-admin seem to get overwritten back to the default ' <blank> ' domain and search domain of ' lan '.

Can someone please tell me what I'm missing.
Thanks
Duncan

---

