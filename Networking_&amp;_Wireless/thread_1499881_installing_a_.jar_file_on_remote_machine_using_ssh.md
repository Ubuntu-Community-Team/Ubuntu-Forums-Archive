---
title: "installing a .jar file on remote machine using ssh"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by mack4 on 2010-06-02
I don't understand what's going on, pls can someone help. 

I have a remote machine with Ubuntu 8.04.1. I have uploaded a .jar file and run it over ssh using java -jar file.jar.

It says that it needs to output to the screen because it's using a gui.

I therefore tried various ways of running X11 on the remote machine as follows:
xterm in a terminal window, then in the x11 window 'ssh -l user -X -v ip.addr'

having logged in, it won't run any x11 apps, even trying xcalc results in "Error: Can't open display: "

---

