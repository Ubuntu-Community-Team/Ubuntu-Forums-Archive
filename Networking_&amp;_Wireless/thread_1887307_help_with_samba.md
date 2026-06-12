---
title: "help with samba"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by antikhrist on 2011-11-26
hi ive been using samba with ubuntu untill a few months ago then one day after an update all my shares stopped working outside of the serving machine im trying to share a video folder with no password or security to both a maverick netbook and a win7 desktop with readwrite access, i was using the samba program from the software center  (if it helps ive also tried with natty and oneric too with the same results)

can anyone help?

---

### Post by dandnsmith on 2011-11-27
At a guess, you're only considering updates to the server (otherwise you may have a lot of sorting out of trails to do), so I'd guess at a security issue - possibly the firewall (which you could disable as a first test).

HTH

---

### Post by antikhrist on 2011-11-30
is there a default firewall in ubuntu? it doesnt seem to affect windows shares when im in there if that makes a diffrence ill check the router too although i think the firewalls already off

---

### Post by dandnsmith on 2011-12-01
check to see if iptables is running - normally the default settings are fairly 'easy', letting through those things which you'd like, but it's work a check to see.

---

