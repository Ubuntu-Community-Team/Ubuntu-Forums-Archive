---
title: "Ubuntu in need of SAMBA easy config tool?"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Janjiss on 2009-07-11
Hello dear ubuntu community!
I work for small IT company in mine town and I am responsible for networking administration. I started to use Linux ~ 1 year ago. I like this system for stability and performance. Now the bad part: It is a hell to configure SAMBA to work well. Shared folders work, but try to share your printer... Maybe Ubuntu needs some kind of easy SAMBA config tool, what do you think? Or maybe there is some kind of manual, wich explains perfectly how to setop your printer with no headaches? If so, post a link and ill try to help sysadmins like myself to swich to linux more easaly. 

Thank you for any reply :)

---

### Post by jonobr on 2009-07-11
Hello


Have you tried webmin?

Its specifically for admins wanting a gui to perform such tasks and general admin of a system.

[Heres the link]("http://www.webmin.com/")
Samba is one of the supported modules and ubuntu is supported under the webmin project.

I dont use it as I feel things like this extract you from the low level interaction with the system including config files and more importantly the ability to view errors and logs and so on which may be hidden by a gui.

However, different strokes for different folks as they say

Cheers

---

### Post by Iowan on 2009-07-12
There is a GUI tool for Samba (besides SWAT), but I'm drawing a blank on what it's called.  (I, too, prefer the old-fashioned config file editing method, as GUI tools can sometimes change things in unexpected ways.)

---

### Post by Janjiss on 2009-07-12
I can do it with configuration files 2. The biggest problem is to find manuals about - How samba actually works. In samba.org you can find ways to configure your server, but you cant find step-by-step guide of basic samba principles. Or maybe i am not searching well?

---

### Post by capscrew on 2009-07-12
A nice tool for managing shares is system-config-samba.  You can read about it [_here_]("http://miltonpaiva.wordpress.com/2008/11/09/samba-how-to-using-system-config-samba-fedora-9/").  The project stated at Red Hat but the package is available in the Ubuntu repos.

---

