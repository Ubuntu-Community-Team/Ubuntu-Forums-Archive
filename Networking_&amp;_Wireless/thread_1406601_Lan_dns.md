---
title: "Lan dns"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2010-02-14
Hi,

Having just scanned loads of other posts, I can't find one that addresses this name resolution issue of mine.

I have a NAS server running Debian with Dnsmasq (local DNS and DHCP service). This is working well, including fetching upstream requests from my ISP's DNS service and caching them locally.

I have another PC not running Ubuntu which happily resolves DNS and non-DNS names.  E.g.
```

[COLOR="Navy"]ping hagrid.
ping hagrid[/COLOR]
```

both work.

However, this is not the case on my Ubuntu PC. It is only able to resolve DNS names, not non-DNS names.  ```
[COLOR="Navy"]ping hagrid.[/COLOR]
``` works but ```
[COLOR="DarkRed"]ping hagrid[/COLOR]
``` does not.

I have the standard nsswitch.conf and host.conf.

Can anyone help me put right my client PC problem?
TIA,
Rick

---

### Post by Iowan on 2010-02-14
The Ubuntu machine uses the same DNS? I seem to recall having similar problems with my dnsmasq server. I don't remember if it was the **domain-needed** option, or the **expand-hosts** option that finally made it work - probably the latter.

---

### Post by rickbeton on 2010-02-14
You're spot on with expand-hosts.  :)

I enabled the expand-hosts option in the dnsmasq.conf file and restarted the dnsmasq service. Now it works fine.

Thanks for the tip!

Rick

---

