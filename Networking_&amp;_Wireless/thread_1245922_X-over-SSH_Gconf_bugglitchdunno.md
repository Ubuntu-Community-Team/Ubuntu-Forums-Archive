---
title: "X-over-SSH Gconf bug/glitch/dunno"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by zoqaeski on 2009-08-21
For some reason, if I run an X program over SSH, it bugs up Gconf.

I can log into SSH with no problems, and starting an X program works too, with the exception of 'Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".' warning messages. 

But when I exit the processes the X-session remains open (I think), and logging out doesn't close the session. On the Ubuntu machine, somehow this messes up gconf and stops it from loading or changing its database. I only notice this because preferences that depend on gconf (such as changing the desktop wallpaper) no longer work until I log out of the Ubuntu machine and back in again.

It's really... odd.

---

