---
title: "Netbios is broken in 9.10?  Really?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by fizgig on 2009-12-14
I can't ping my ubuntu computer from my xp box.  The ubuntu computer can, however resolve the xp name and ping it just fine.

I found a guide that said to change a line in /etc/nsswitch.conf from **hosts: files dns** to **hosts: files dns wins**

Trouble is, my hosts line looks like this:

**hosts:  files mdns4_minimal [NOTFOUND=return] dns mdns4 wins**

and appears to have wins already in it.  Is that NOTFOUND part screwing me up?

---

### Post by dmizer on 2009-12-15
The hosts line does lookups in order of things that appear in the hosts line. The NOTFOUND=return option simply does a double take on "files" and "mdns4_minimal" if they fail the first time through.

DNS queries your router or your ISP's DNS servers, so if you want wins lookups to work correctly, you'll need to put wins in front of dns like this:
```
hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```
However, if you do have a local DNS server, the above configuration could cause problems and hangs during boot. It could also cause hangs and problems during boot if you are running a local firewall.

Odds are, if you're relying on wins for name resolution, your network is behind a hardware firewall which means that a local software firewall is unnecessary. If you have something like firestarter installed, I highly suggest removing it.

More information on the order of wins and dns in this line can be found here: [http://ubuntuforums.org/showpost.php?p=7255859&postcount=15](http://ubuntuforums.org/showpost.php?p=7255859&postcount=15)

---

