---
title: "mythfrontend segfaults"
date: 2009-04-20
forum: Mythbuntu
---

### Post by dakota34 on 2009-04-20
I uninstalled mythfrontend on my desktop when I removed a secondary backend I had running on the same pc. Primary backend is fine, as are the other mythbuntu frontends in the house (which I left alone thank deity) however upon re-installing the frontend on my desktop via control-centre I'm now seeing a segfault everytime I try to run mythfrontend. I upgraded to Jaunty hoping this might auto-magically fix it but no magic occurred. 

All other frontends in the house are running fine, it seems to be removing and re-installing that caused the problem... seems to make the db connection fine, then splat.  

Any suggestions welcome...

john@john-desktop:~$ mythfrontend
2009-04-20 10:38:55.640 Using runtime prefix = /usr
2009-04-20 10:38:56.446 XScreenSaver support enabled
2009-04-20 10:38:56.452 DPMS is active.
2009-04-20 10:38:56.453 Empty LocalHostName.
2009-04-20 10:38:56.453 Using localhost value of john-desktop
2009-04-20 10:38:56.454 Testing network connectivity to 192.168.0.7
2009-04-20 10:38:56.494 New DB connection, total: 1
2009-04-20 10:38:56.497 Connected to database 'mythconverg' at host: 192.168.0.7
2009-04-20 10:38:56.501 Closing DB connection named 'DBManager0'
2009-04-20 10:38:56.508 Primary screen 0.
2009-04-20 10:38:56.509 Connected to database 'mythconverg' at host: 192.168.0.7
2009-04-20 10:38:56.511 Using screen 0, 1680x1050 at 0,0
2009-04-20 10:38:56.528 New DB connection, total: 2
2009-04-20 10:38:56.529 Connected to database 'mythconverg' at host: 192.168.0.7
2009-04-20 10:38:56.539 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-04-20 10:38:56.539 Enabled verbose msgs:  important general
Segmentation fault

---

