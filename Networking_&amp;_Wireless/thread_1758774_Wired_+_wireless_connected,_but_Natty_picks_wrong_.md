---
title: "Wired + wireless connected, but Natty picks wrong network for Internet"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by noah++ on 2011-05-15
Hi,

I have a wireless network (192.168.1.0) that's bridged to the Internet and a wired one (192.168.0.0) that's only local. When I am connected to both networks, Natty wants to route my Internet traffic through the wired, local-only one.

Can I make it automatically "just work", so that the right network is chosen for Internet traffic? Otherwise, what's the workaround?

---

### Post by noah++ on 2011-05-15
Found a workaround, but would still appreciate a just-works fix.

_Workaround:_

[LIST]
[*]Left-click network indicator applet
[*]Choose **Edit Connections...**
[*]In the window that now appears, highlight the local-only network name and click **Edit...**
[*]In this new windows, choose the **IPv4 Settings** tab.
[*]In there, click the **Routes...** button.
[*]Check the box for **Use this connection only for resources on its network**
[*]Save changes & allow this network to automatically reconnect.
[*]Manually reconnect to the other, Internet-bridged network.
[/LIST]
Naturally, there's some inconvenience associated with this solution when I am roaming and my wired connection supplies the Internet.

---

### Post by noah++ on 2011-05-19
Interestingly enough, this article was published on Slashdot soon after I made this post.

[http://tech.slashdot.org/story/11/05/17/2355256/How-Windows-7-Knows-About-Your-Internet-Connection](http://tech.slashdot.org/story/11/05/17/2355256/How-Windows-7-Knows-About-Your-Internet-Connection)

Windows queries microsoft.com to test if a connection has Internet connectivity. It also lets the user change the query target. Doesn't sound too hard to implement.

---

### Post by rachel1.0 on 2012-04-28
> **noah++ said:**
> Found a workaround, but would still appreciate a just-works fix.

_Workaround:_

[LIST]
[*]Left-click network indicator applet
[*]Choose **Edit Connections...**
[*]In the window that now appears, highlight the local-only network name and click **Edit...**
[*]In this new windows, choose the **IPv4 Settings** tab.
[*]In there, click the **Routes...** button.
[*]Check the box for **Use this connection only for resources on its network**
[*]Save changes & allow this network to automatically reconnect.
[*]Manually reconnect to the other, Internet-bridged network.
[/LIST]
Naturally, there's some inconvenience associated with this solution when I am roaming and my wired connection supplies the Internet.


Thanks for posting your solution here, a year and probably 2 versions of ubuntu later, it was still useful to me (I have the exact same config here). I'd upvote you if it was possible :)

---

