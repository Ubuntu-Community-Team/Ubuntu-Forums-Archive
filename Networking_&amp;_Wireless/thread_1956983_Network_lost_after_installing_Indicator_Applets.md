---
title: "Network lost after installing Indicator Applets"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2012-04-11
I was jumping for joy when I saw that you can get back to a normal Gnome desktop by using Gnome Classic (no effects).  It was my understanding up until today anyway that the desktop was "locked", but I found out that if you turn off compositing you can in fact move applets and panels around :guitar:

But the issue I'm having now is that after installing the indicator applets from here

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

my network dies and I can not figure out how to bring it back up, with or without the indicator applet running.  PLEASE HELP!!!

---

### Post by N00b-un-2 on 2012-04-12
nevermind.  I fixed it.  the issue arises from connman installing itself as a dependency of network indicator.  Removed that, and then downloaded both network-manager and network-manager-gnome (downloaded on another computer and put on a thumb drive)  After that, network works again.

---

