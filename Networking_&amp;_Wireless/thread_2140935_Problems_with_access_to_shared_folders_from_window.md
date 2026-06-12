---
title: "Problems with access to shared folders from windows share"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by Tor Andersen on 2013-05-01
Hey.

I have an Iomega Home Media server where I have saved all my files. The various folders I Mount with ease. This is done automatically by stab during startup. Mounts looks like this:

/ / iomega-0e568d/music / media/Musikk2 CIFS username = user, password = psw, rw, iocharset = utf8, file_mode = 4777, dir_mode = 4777 0:00

As you can see I have used chmod 4777 that should allow full access to all.

Access I have, and can open and close files and save to existing folders without problems. Problems arise when I create a new folder and should take this into use.

The new folder appears in Nautilus with a padlock, and I'm not allowed to store anything in it.

When I open Nautilus with gksudo, I see that the owner is "nobody". I can then set the owner to "root" and give all access, and directory functions normally. I am, however, not allowed to set my own user as owner.

This is somewhat cumbersome, and I'd much appreciated if anyone could help solve the problem.

---

