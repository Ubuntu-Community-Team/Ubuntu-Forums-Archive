---
title: "Moblock+Blockcontrol+Mobloquer"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by 13east on 2011-07-14
I have almost all of the default lists available to be blocked except for "fornonlancomputers" and "rapidshare". I have also manually added the "Zeus" list from iblocklist.com. I also have the "http" and "https" ports on a whitelist.
[LIST]
[*]Should I have the above two lists enabled to block as well?

[*]Should I remove some of the default lists as being redundant?

[*]Are there any sites other than iblocklist.com that maintain a decent list of anti-P2P IP ranges?

[*]What IP-ranges should I maintain on a whitelist to ensure smooth web-surfing/streaming/torrent-downloading while still maintaining my privacy?
[/LIST]

EDIT:

Plus = How do I add multiple blocklists to whitelist (i.e. Steam and PirateBay) so they're maintained with new IP-ranges as the list is updated?  I don't want to have to add IP-ranges to allow.p2p as it is that I would have to manually add new IP-ranges as they become available.

---

### Post by jre on 2011-07-24
IMHO you are using much too many lists. The default set is already quite paranoid.   But I can't give you clear advice on this.
I'm not aware of any blocklist that is not available on iblocklist, since iblocklist also mirrors other blocklists.
Having http and https whitelisted is a security risk on its own, although most people have this. The safer way is to whitelist IPs - just whitelist them from mobloquer, whenever a safe site that you wanted to visit was blocked.

I plan to integrate automatic allowlist management for pgl (successor of moblock,...), but yet this isn't implemented.

---

### Post by 13east on 2011-07-24
> **jre said:**
> IMHO you are using much too many lists. The default set is already quite paranoid.   But I can't give you clear advice on this.
I'm not aware of any blocklist that is not available on iblocklist, since iblocklist also mirrors other blocklists.
Having http and https whitelisted is a security risk on its own, although most people have this. The safer way is to whitelist IPs - just whitelist them from mobloquer, whenever a safe site that you wanted to visit was blocked.

I plan to integrate automatic allowlist management for pgl (successor of moblock,...), but yet this isn't implemented.

thx for the advice...
I'm waiting on pgl2+gui to come out as well but until than this looks like the best optiion

---

