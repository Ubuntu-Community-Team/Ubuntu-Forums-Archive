---
title: "Login Session Does not appear.."
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by imran65 on 2009-06-04
Hi, I m having a problem with my ubuntu 9.04. When i start the system, it is not going to sign-on session, but directly to command prompt for log-in. Once i enter my user id and password, i run the command "startx" but it gives me message, 
X: /tmp/.X11-unix has suspicious mode (not 1777) or is not a directory, aborting. giving up.
Xinit: No such file or directory (errorno 2): unable to connect to X server.
Xinit: No such process (errorno 3): Server error.
and brings me back to command prompt, at current, i m solving the issue as, 
"chmod 1777 /tmp/.X11-unix" every time and run the command "startx" again, it opens the session. i m using KDE4.

---

