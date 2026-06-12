---
title: "How do I take screenshots of myttv?"
date: 2008-09-13
forum: Mythbuntu
---

### Post by Andrew U.K. on 2008-09-13
Hi,
I would like to take a screenshot of some mythbackend setup pages. How do I bring up the terminal so I can import -window.

Thanks 
Andrew

---

### Post by managementboy on 2008-09-15
> **Andrew U.K. said:**
> Hi,
I would like to take a screenshot of some mythbackend setup pages. How do I bring up the terminal so I can import -window.

Thanks 
Andrew

you mean any terminal? xterm
then:
tail /var/log/mythtv/mythbackend.log

but I would not call it a screenshot... its just the logs.

---

### Post by Andrew U.K. on 2008-09-15
Thanks, but I've seen screenshots of mythbackend setup pages. The window is reduced in size and you can see the toolbar of the desktop above. So really the question is how do I re-size the setup window?

Thanks 
Andrew

---

### Post by db260179 on 2008-09-15
Open a terminal, type as follows

sudo /etc/init.d/mythtv-backend stop && mythtv-setup.real --geometry 800x600



> **Andrew U.K. said:**
> Thanks, but I've seen screenshots of mythbackend setup pages. The window is reduced in size and you can see the toolbar of the desktop above. So really the question is how do I re-size the setup window?

Thanks 
Andrew

---

### Post by fenian on 2008-09-16
Is there a print screen button on your keyboard?On mt keyboard F13 will take a screenshot.

---

