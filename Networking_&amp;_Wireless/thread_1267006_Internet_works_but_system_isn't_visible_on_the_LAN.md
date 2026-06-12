---
title: "Internet works but system isn't visible on the LAN (wifi)"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by villalbator on 2009-09-15
Hi all,

I've been searching through the forum but I didn't find a solution

I've got a Zotac Ion system with Ubuntu Jaunty and XBMC connected by wifi only. Wireless connectivity is ok because I can browse webs with mozilla, and in XBMC the weather section, rss, and imdb scrapers work fine. However, I can't reach my Zotac from any other system [IMG]http://xbmc.org/forum/images/smilies2/baffled5wh.gif[/IMG]

When I try a ping to the Zotac from my macbook or my windows PC, the host is always down.
I've discarded problems with the router because I always can reach the macbook (wifi only) from any other machine.
First, I thought that it could be a problem with iptables / ufw so I disabled it, but the problem was still there.

I've done a lot of tests and I've found something curious:
If I try a ping from the Zotac to another machine (even the router or the Zotac itself) the answer is ok.
Since this point, the Zotac is then reachable from any system, so I can go into it with SSH on my macbook. The problem is that this solution doesn't last forever. In the next hours/minutes (I'm not sure the exact period) the Zotac is not reachable again.

It must be something about wifi driver or similar but I'm a newby in Linux.
When I tested a wired connection the problem didn't appear.

Any ideas?
Thank you in advance?

---

### Post by villalbator on 2009-09-15
Ok, I've just solved the problem

For those with similar issues, install wicd.
It works perfect and much better than network manager

---

