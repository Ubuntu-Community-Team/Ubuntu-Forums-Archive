---
title: "Using gedit on telnet"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by mariopoeta on 2012-02-01
hello,
I am using telnet , and i wanna make gedit comand to a file which is in the other computer and then appear Gtk-WARNING **: cannot open display:.
This errror appear when i am using zenity or dialog too.
And i wanna make that without using a SU/root and SSH, is that possible?


Or there is another comand or utility to send messages like popups to another pc in the network?

---

### Post by aromo on 2012-02-01
You need to open a graphic session to the other server.  Telnet and SSH are text-based connections.  You can run vi, though.

---

