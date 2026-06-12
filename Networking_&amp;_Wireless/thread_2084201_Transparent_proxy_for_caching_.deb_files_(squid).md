---
title: "Transparent proxy for caching .deb files (squid?)"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by chronos00 on 2012-11-14
Hi everyone,

I have looked for this for a very long time now, and I am still empty handed. Thus, I seek the help of fellow Ubuntuers.

In a nut shell, I am looking for a way to cache .deb files on my network in a transparent way, so that commonly installed packages consume less bandwidth and time to download. Of course this will probably be achieved with squid. The question is how.

If one computer upgrades package A to the latest version, then this package should be cached. The next computer that wants to download and upgrade package A, should access this file through the cache, avoiding to re-download.

The catch is I want to do this in a transparent way for the clients, so that I don't have to configure anything on their side.

The other problem I found is that with regular file-caching, one .deb file at ubuntu.com is not the same as the same file located at ubuntu.com.ar. And this applies to any repository in the world.


I have seen many solution based on generating my own repository on my server, and then configuring this repository on all the clients. Other solutions based on client-server programs ([squid-deb-proxy]("https://launchpad.net/squid-deb-proxy")), etc. But as I said, I would like this to be a transparent solution.


Any ideas are greatly appreciated!
Thank you in advance.

---

