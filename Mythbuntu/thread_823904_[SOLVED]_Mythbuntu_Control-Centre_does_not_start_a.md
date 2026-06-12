---
title: "[SOLVED] Mythbuntu Control-Centre does not start anymore"
date: 2008-06-09
forum: Mythbuntu
---

### Post by Familienvater on 2008-06-09
I have installed Mythbuntu 8.04 on an existing Ubuntu 8.04 Installation. I am using it as a Frontend, the backend is a different machine.

When I try to start Mythbuntu-Control-Centre I see its window for about half a second. Then it's gone...

I tried to start it from the terminal. The result was the same. I did not get any error message.

The Control-Centre used to work. I have no idea why it's not working anymore. Does anybody have an idea where to start?

Regards,

Familienvater

---

### Post by laga on 2008-06-09
Hi,

please open a terminal and enter the following: 

```

sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre

```

You should get some error messages in the terminal telling you what failed. If you post these here, I'm sure we'll be able to fix it.

Regards,

Michael

---

### Post by Familienvater on 2008-06-09
Michael,

I get no error messages this way. It actually works! And what is even more strange - now the window stays open after I opened the Control-Centre in the menu??? Nobody will believe, but I experienced this behaviour in the last 2 days. And now it's gone?!?

Nevertheless, thank you very much for your help!

Regards,

Familienvater

---

### Post by tyoung75 on 2009-05-18
Hi,

   I'm having the same problem after a crash and restore from backup. Here's my error message:

Traceback (most recent call last):
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 26, in <module>
    from MythbuntuControlCentre.core import ControlCentre
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 35, in <module>
    import MySQLdb
ImportError: No module named MySQLdb

Can anyone help?

Cheers,

Tim

---

