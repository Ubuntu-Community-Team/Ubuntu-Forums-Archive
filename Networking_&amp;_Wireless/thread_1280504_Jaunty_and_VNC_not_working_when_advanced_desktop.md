---
title: "Jaunty and VNC not working when advanced desktop"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by jpgoossen on 2009-10-02
Hi,

Am using Jaunty on a desktop and on a notebook. One runs Gnome as desktop environment, the other KDE. Both machines are located at my home, connected to the same network. Both have remote Desktop (Gnome Remore Desktop 2.26.1) enabled. 
I often have to log into the machines remotely. This I need to do from a Windows XP notebook, using RealVNC viewer.
In itself, this works fine.

The only thing is that, if I have any advanced desktop settings enabled on the remote machines, the remote session locks up right after logging in. Be it Emerald, Compiz, Plasma, none will work.

All the eye candy and handy settings need to be disabled to be able to actually use the machines remotely. For remote usage that is fine, but I would like to enable those advanced settings for local use.

Mind you, connecting goes fine, whether advanced desktop is enabled or not on those computers. It is just, as soon as I have logged in and see the desktop of the computers I have logged into, the screen "freezes". Both on the KDE as on the Gnome machines. If I use the desktops in the most default state, I can log in and actually use the computers.
Advanced settings enabled, I can log in and Freeze frame. I do see the dot of the local mouse pointer moving, but not clicking or anything else will get any effect. When I logout and log back in, I see that the screen has changed, so it is not that the computer actually froze. It is just the screen that is useless.

ANy ideas?

TIA, Patrick

---

### Post by spacesearcher on 2009-10-12
I have the same problem and so do a bunch of other people. Here is a bug report of the problem [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

If you read that you might get some more info. I don't think there is a good fix yet.

---

