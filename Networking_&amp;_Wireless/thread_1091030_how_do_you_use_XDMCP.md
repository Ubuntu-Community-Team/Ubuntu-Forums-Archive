---
title: "how do you use XDMCP?"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by cmoney12051 on 2009-03-08
Im pretty new to this linux stuff, i started using it about 3 months ago, cause im tired of microsoft, and vista just sucks! So anyway, what im trying to do here is to get my dell inspirion 1501 laptop running ubuntu 8.10 to be remote controlled via my eee pc 701 running ubuntu 8.10 via XDMCP. I enabled remote connection in the login window setting in administrator, and restarted the dell laptop, and eee pc, and when i try to go to options and connect via XDMCP it loads to the searching screen, but it never finds my dell laptop, or itself. They are both on a wireless network, and no matter what i do, i can never get it to work. please help

---

### Post by langerak on 2009-05-16
If wireless then make sure that in ur router settings, the opton CTS protection is disabled, when enabled this forbids clients connected to it from seeing other clients. Also, when set as AP it forbids it as well. At least that was a solution for my same problem :). Also remember that u have to edit /etc/gdm/gdm.conf and /etc/ssh/ssh_config, these 2 are the most important files to get XDMCP working, since TCP requests are disabled by default and can be enabled within these 2 files :).

---

