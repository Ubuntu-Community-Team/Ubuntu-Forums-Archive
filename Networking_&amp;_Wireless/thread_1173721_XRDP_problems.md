---
title: "XRDP problems"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by itFinallyWorks on 2009-05-30
I am trying to setup an XRDP server on a Jaunty install.  After working around this bug: [https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/375755]("https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/375755") I was able to log in - and it actually works!  Until I reboot.

When I reboot I run into [https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/339032]("https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/339032").  If I manually go in and restart xrdp via the init.d script it complains about the pid files for xrdp and sesman.  After clearing them (or editing the script to do so), the service restarts and I can login again (yay).  But I want to be able to have this thing come up automatically on its own.  Any tips for debugging or workarounds?

Thanks

---

