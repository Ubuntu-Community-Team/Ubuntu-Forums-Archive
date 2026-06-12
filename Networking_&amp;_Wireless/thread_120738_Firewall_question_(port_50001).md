---
title: "Firewall question (port 50001)"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by Aybara on 2006-01-23
Hi!

I just installed Firestarter to add some security to my Ubuntu.

Now I get a lot of Blocked Connections from ports 50001, 1900 and 8008. Anyone got an idea what these connections are? Something I should open up?

---

### Post by mips on 2006-01-23
1900=SSDP, Simple Service Discovery Protocol
8008=HTTP Alternate, Hyper Text Transfer Protocol
50001=???, Some type of client/server port.

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://www.seifried.org/security/ports/](http://www.seifried.org/security/ports/)

> Now I get a lot of Blocked Connections from ports 50001, 1900 and 8008. Anyone got an idea what these connections are? Something I should open up?

That's up to you but you don't need them. Depending on your level of vigilance/paranoia you should actually disable all ports by default and only open up what you need...

---

### Post by darth_vector on 2006-01-23
it pays to be paranoid with your firewall. check out the "i got hacked" posts in the security forum.

---

