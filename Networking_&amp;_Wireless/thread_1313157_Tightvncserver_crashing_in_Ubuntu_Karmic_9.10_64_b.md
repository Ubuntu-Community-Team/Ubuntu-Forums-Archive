---
title: "Tightvncserver crashing in Ubuntu Karmic 9.10 64 bit"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by rmccarri on 2009-11-03
Hi Everyone,
I'm sending this post out as an inquiry as to how to troubleshoot a tightvncserver crash.  It's crashing almost instantly when I connect via an ssh tunnel.  I've done some searching of the log files and cannot find any error messages to get a handle on the problem.  All I'm getting on the remote side is a message that the vnc server closed the connection.  In the .vnc directory, there's nothing in the log file to hint at what might be going on.  Any help in pointing me in the right direction would be very appreciated.
Thanks,
Rob

---

### Post by rmccarri on 2009-11-03
Hi everyone,
I tracked down the error to the crash in /var/log/message

Apparently, I'm getting a glxinfo segmentation fault which causes a xtightvnc segmentation fault.  Is anyone else having this issue?
Rob

---

### Post by rmccarri on 2010-02-01
Hi everyone.
I'm still having this issue and thought that I would bring it up again.

When I connect to my home server via a VNC connection, everything is fine for a while, but eventually I get a segfault from glxinfo and Xtightvnc.  Is anyone else having this issue or has found a fix?
Thanks!
Rob

---

### Post by rmccarri on 2010-02-02
So checking into things, it seems that Tightvnc does not support OpenGL.  I wonder if there is a way to change the xstartup file so that the desktop session that spawns does not use opengl?  Maybe there are some other ways around this?  I tried using vnc4server instead of tightvnc and it was way too slow.

---

