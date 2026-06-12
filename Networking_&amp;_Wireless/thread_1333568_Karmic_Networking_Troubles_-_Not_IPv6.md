---
title: "Karmic Networking Troubles - Not IPv6?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Andysan on 2009-11-21
Hi all,

I upgraded from Ubuntu Jaunty to Karmic on my Acer Aspire D150 netbook a few weeks back and the networking hasnt been working correctly ever since.

Symptoms
[LIST]
Web browsing is super slow - this has been fixed by using the OpenDNS servers.
Update manager is borked - gives a   404  Not Found [IP: xxx.xxx.xxx.xx.xx]
Cannot browser my windows network - gives a Failed to retrieve share list from server error.
[/LIST]

When u run the following code I dont get any output which makes me think IPv6 is not the problem, but if so then I dont know what is:

```
lsmod | grep inet6
```

I've tried my other netbook older AAO running Intrepid on the same network and it runs fine.  Any help would be much appreciated as Im having to use Windows at the moment.  I have Googled the problem but just keep coming up with how to check for IPv6 and I keep coming up negative.  I'm sure its DNS related though.

Cheers.

---

### Post by Andysan on 2009-11-22
In case anyone is having the same trouble, I reinstalled Karmic via a fresh install instead of an upgrade from jaunty and this seems to have fixed all problems.

---

