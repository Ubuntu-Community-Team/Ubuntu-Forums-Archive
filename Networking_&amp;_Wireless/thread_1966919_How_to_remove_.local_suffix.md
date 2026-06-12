---
title: "How to remove .local suffix"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by duncang92 on 2012-04-27
I use an old Dell PC as a "server" to download, store and serve movies, music etc. to an HTPC and three old XBox's all running XBMC.

The movies, music etc. are all then stored on several drives and folders shared over SMB.

I was using Windows XP on the Dell PC and since it's rather slow and old decided to upgrade to Ubuntu 12.04. I want to seamlessly move from Windows to Ubuntu without having to change the rest of my network/appliances.

When I was running Windows I would access the share on the Dell PC using "kitchen" ..... I now have to use "kitchen.local" and after much reading I think I'm more confused than when I started.

How do I remove the .local tld requirement?

Cheers, Duncan

---

### Post by papibe on 2012-04-27
Hi duncang92.

I see the following reasons you need to use .local:
[LIST=1]
[*]Your router does not provides DNS, or/and
[*]There's a problem with your Samba installation on your server.
[/LIST]
Could you post the results of these commands on the server:
```
ifconfig

nslookup ubuntu.com

ps aux | grep nmbd
```
Regards.

---

