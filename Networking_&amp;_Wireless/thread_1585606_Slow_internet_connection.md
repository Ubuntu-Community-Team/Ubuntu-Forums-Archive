---
title: "Slow internet connection"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by fourwood on 2010-09-30
In the last week or so I've had a weird problem on my 10.04 desktop where web browsing (and possibly other network-related traffic) is painfully slow and flaky. DNS lookups seem to go okay, but Firefox can sit there at "Connecting to <domain>..." and "Waiting for <domain>..." for upwards of a minute before loading a page or parts of pages (images on a separate subdomain, etc.). Occasionally pages will just time out and not load at all. The kicker is that this even happens when trying to connect to my router. After typing in 192.168.1.1 I'll usually have to wait at least 15 seconds or so for even the login box to pop up.

This wasn't an issue until something like a week ago. I don't seem to have the problem on my Dell laptop with 10.04 installed. I'm running a ~4 year old home-built desktop using a Linksys WMP54G PCI wireless card for networking. I had Ubuntu x64 installed through Wubi when this first cropped up. I reinstalled as a native x86 installation and still have the same problem. It's also not just Firefox; Chrome has similar issues and IMing through Empathy can get dicey. I've even tried creating a new user to try starting with a fresh home directory, but that didn't change anything.

Oh, and finally, it all works just fine in Windows 7 x64.  I would just hate to be stuck using Windows now that I've gotten used to using Ubuntu all the time.

Anyone know what could be wrong? Thanks in advance.

---

### Post by gordintoronto on 2010-09-30
Is there any chance a neighbour has set up a router on the same channel?

---

### Post by fourwood on 2010-10-05
I definitely hadn't thought of that option.  I switched to a new channel and network connections seem snappy again.  

Thanks for the suggestion.

---

