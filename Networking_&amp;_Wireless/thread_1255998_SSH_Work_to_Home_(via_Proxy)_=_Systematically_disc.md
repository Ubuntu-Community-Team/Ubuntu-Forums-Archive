---
title: "SSH Work to Home (via Proxy) = Systematically disconnected after a short while !?"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by TomG on 2009-09-02
Hi,

I setup **OpenSSH **on a mini server at **home **(powered by Crunchbang). This works fine.
However **when I connect from WORK I'm disconnected very quickly** after a few dozens of seconds...

As summary the ways I connect :

  **Home PC (ubuntu) --> Home Router --> internet (via dyndns) --> Home Server   : Everything is OK, never been disconnected**

    **Work PC (windows with putty or winscp) --> Proxy --> internet (via dyndns) --> Home Server : Connection OK but systematicaly disconnected after 1-2 minutes**

I browsed the web and tried a few "keep alive" parameters/tricks but no way.
I also tries to setup debug traces into Putty and Winscp but I cannot find something strange.
I suspect Work proxy/firewalls but does anyone know how to diagnose and fix this ?

Thanks,
Tom

---

