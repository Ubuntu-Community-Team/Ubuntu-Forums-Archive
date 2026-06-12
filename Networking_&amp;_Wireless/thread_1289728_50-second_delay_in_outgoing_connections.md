---
title: "50-second delay in outgoing connections"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by philpem on 2009-10-12
Hi guys,
I could do really with the help of a network guru here...

I'm using an ASUS Eee 1000H laptop at both home and university. It's running Ubuntu 8.10, and has 2GB RAM.

Connecting to my home wireless network works fine on both Windows XP and Ubuntu.

However, when I connect to the university WiFi from Ubuntu I get strange effects with outbound connections. Specifically, there's about a 50-second delay between me initiating a HTTP request and any data appearing from the other end.

HTTPS requests (port 443) -- or even outbound SSH connections on port 443 (!) are unaffected by this madness.

On Windows, the wireless works fine. I can access the web and everything works more-or-less fine. It just seems to be a "Linux thing" as Computing Services put it.

Outbound network access is controlled by a Cisco router of some kind which presents a web page asking for authentication, then switches to allowing packets through via a transparent proxy (which appears to be the same machine that's doing the authentication request).

Question: Is there something anyone can think of that might cause this sort of delay in connections? I can probably post a couple of tcpdump / Wireshark logs if they'd be useful.

Also, it's not just Firefox, etc. that's affected -- it affects apt-get as well.

Cheers,
Phil.

---

