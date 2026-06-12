---
title: "No networking"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by Arkold Thos on 2010-07-02
Heya, I am having the following problem with a bland new Kubuntu installation with the newest KDE packages and stuff

The problem is that _I CANNOT_ launch networking once the system is running with the following methods

start networking : stop/waiting
ifup eth0 : no eth0=eth0
ifdown eth0 : Interface doesn't configured (or smth alike)

when that happens, I'm unable to see eth0 by using ifconfig, the only method I found for making it work, is booting in single user mode, then use netroot, then exit and resume the startup, and it works!

... however, is quite annoying that i cannot reconfigure the connection when the system is up, any idea? -- I been using Debian since 4 yrs ago and Ubuntu since 2, first time i get this

---

