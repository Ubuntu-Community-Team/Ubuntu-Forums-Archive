---
title: "why isn't internet so speedy in ubuntu?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by akh00 on 2009-01-11
Under XP, my 2mbps connection works fine with the promised speed. But in ubuntu it feels lazy and drops to a terrible slow speed. why is this so? are there any configs to change?

---

### Post by Iowan on 2009-01-11
One *possible* reason might be IPv6.  My signature has a (somewhat dated) link on disabling it - or you can search the forum for something more current.

---

### Post by ubiDD on 2009-02-02
I had the same problem; I went two routes:  I installed wicd for my connection manager and Tomato firmware on my router.
I've tried messing around with ndiswrapper to no avail, network manager wouldn't work properly with WPA2, and the router's native firmware doesn't recognize IPv6.  I tried blacklisting IPv6 but had some other issues with my install that I decided to reinstall Ubuntu, and currently don't have it blacklisted.

Network hardware:
Linksys WMP54G v1.1 adapter (who doesn't like a broadcomm challenge?)
Linksys WRT54G v3.1 router

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")
[http://www.polarcloud.com/tomato]("http://www.polarcloud.com/tomato") (be careful with this one if you've never updated router firmware before)

edit: I realize it doesn't look all that fast, but my bandwidth is the lowest tier offered by my ISP at 1.5 megs :P

---

