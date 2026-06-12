---
title: "Wireless shuts down occasionally"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Toriam on 2010-04-23
Sometimes, the built in wireless function on my acer aspire one doesn't start up. When i left click in the nm-applet icon, either it displays that the wireless is disabled (no check in the box), or it says nothing about wireless, sometimes sliding the little slider at the front right over does the trick, sometimes that doesn't do any good. Sometimes it just dies while the computer is on. Sometimes it just won't connect to a network. It just seems a little unstable. What causes this, and how can I make it stop happening? I tried to restart nm in terminal, and got these goodies...


.toriam@acer:~$ nm-applet

** (nm-applet:1497): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:1497): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

toriam@acer:~$ sudo nm-applet
[sudo] password for toriam: 

** (nm-applet:1552): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

What next? Thanks for reading this!
If things keep messing up, is there something better I can use?

It's working at the moment, but help me on this so I can prevent it in the future.

---

### Post by bobyy on 2010-04-23
Hy
you can try WICD like network manager

Regard`s

---

