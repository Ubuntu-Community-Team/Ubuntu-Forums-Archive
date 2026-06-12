---
title: "Couldnt see GNOME after install of nvida driver for hardy"
date: 2009-08-08
forum: Multimedia Software
---

### Post by tuckeroil on 2009-08-08
Hey everyone,

It seems when I tried to install the nvida driver for a GeForce 7300GT on my brother's computer, the GUI got broke.  

First before I ran the install I backed-up the /etc/init.d folder, just in case. Then I stopped the GUI with sudo /etc/init.d/gdm stop. Then ran the install using the sh command

Well the install seemed to go just fine but then once the computer rebooted, it came to a black screen.  CTRL + F1 does give me the command line.

I have tried sudo /etc/init.d/gdm start and /gdm restart and both say the X-server is running.  I have always restored my original init.d folder to see if that helped. any ideas? Thanks.

---

