---
title: "leave a program running after i logoff ssh"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by bigdee973 on 2011-10-17
hey sometimes i run a program that takes long. such as a zero fill or downloading a huge file via terminal thru ssh.  sometimes i need to logoff...if i logoff will the command/process continue? if not how can i have the remote PC continue its processes even after i have logged off ssh

---

### Post by matt_symes on 2011-10-17
Hi

Check out screen (with attach and detach).

Kind regards

---

### Post by kaldor on 2011-10-17
Yep, learn about *screen*.

It takes a little getting used to but it does exactly what you need. Anything running in a *screen* session stays active. When reconnecting to that box, you use *screen -ls* and then *screen -r* with the proper entry.

Sounds weird, but try it and you'll see what I mean.

---

### Post by azmyth on 2011-10-17
Interesting, never knew about this. I'd always open new sessions. Here's the tutorial I looked at to get a better idea of what screen does.

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

