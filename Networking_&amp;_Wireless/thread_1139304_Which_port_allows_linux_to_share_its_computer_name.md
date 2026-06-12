---
title: "Which port allows linux to share its computer name."
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by vewert on 2009-04-26
I'm not to familiar with networking, so sorry if my question has an air of ignorance to it.  

Basically, I have a home network, with some Windows machines and a Linux machine.  I mainly use my Linux machine as a server, for running MySQL, Apache, bugzilla, SVN, etc.  I would like my Windows machines, to be able to access the Linux machine by name, instead of by IP.  This works fine if I have the Linux Firewall configured to allow incoming traffic, but doesn't work when I set it to deny incoming traffice (then I can only access by IP).  This leads me to believe that Linux must listen on some port to share its name.

I have set up rules to allow the basic set of ports to be able to access my services (e.g. 21, 80, 5900, 3690) which work when I set to 'deny incoming traffice', but I can only access by IP.

Any suggestions would be appreciated.

---

