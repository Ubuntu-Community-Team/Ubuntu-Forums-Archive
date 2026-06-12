---
title: "edna not serving pages"
date: 2008-09-07
forum: Multimedia Software
---

### Post by Ed J on 2008-09-07
I'm trying to run edna music server on my ubuntu machine.  I edited the edna.conf file to use default templates, resources, set the dir for the mp3 files, ran edna.py in terminal.  edna says its "serving on port 8080..." When I use another PC on my LAN to browse (firefox) to the ip addr of the edna server I get nothing until the browser times out. Firewalls disabled, LAN is good. Tried 192.168.1.22/8080 and 192.168.1.22. 
 Any suggestions?

---

### Post by tehbeyond on 2008-11-02
I realize this post is kind of old and you may have already found the solution, but here is the fix:

Instead of checking 192.168.1.22/8080, you need to check 192.168.1.22:8080.

It needs to be a slash instead of a colon.  I made the same mistake when I started using edna, so don't feel too bad.

---

