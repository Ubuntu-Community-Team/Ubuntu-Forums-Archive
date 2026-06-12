---
title: "Apache2 DirectoryIndex?"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by h4x0rmx on 2010-05-06
I just installed Apache2 with PHP5 through apt-get. It works perfectly fine, but I was trying to configure it and I couldn't find some directives, specifically the "DirectoryIndex".  I want it to serve index.php before it tries to look for index.html
It seems like this installation keeps different parts of the configuration in different files, which seems pretty interesting, but I couldn't find what I wanted to edit.
I looked in /etc/apache2/apache2.conf
ports.conf
conf.d
sites-available/default

Where should I look for it?  Or do I just added? If so, in what file do I need to add it?

Thanks!

---

### Post by h4x0rmx on 2010-05-06
Nevermind!
I just found it... it was under /etc/apache2/mods-enabled/dir.conf

---

