---
title: "Remote desktop, command line options"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by w1z4rd on 2006-07-06
I have to connect daily to about 40 different MS servers, and to admin them I use remote desktop to connect to them. Im busy setting up a whole lot of bash scripts to enable me to quickly connect to them... however... I seem to be fuddling up the options somewhere.

> rdesktop: A Remote Desktop Protocol client.
Version 1.4.1. Copyright (C) 1999-2005 Matt Chapman.
See [http://www.rdesktop.org/](http://www.rdesktop.org/) for more information.

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)


Now, I want to login automaticaly with my script, so I need it to enter the username/password and server its connecting to...

I tried:

> # rd -u myadminaccount -p mypassword myserver.co.za

That doesnt work :/ how would this work correctly? Dankie!

---

### Post by w1z4rd on 2006-07-06
ignore this, got the command wrong

should b rdesktop etc etc

---

