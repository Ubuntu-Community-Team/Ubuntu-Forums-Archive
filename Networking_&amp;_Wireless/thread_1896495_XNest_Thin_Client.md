---
title: "XNest Thin Client"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by coolguy918 on 2011-12-17
For a project, I'm trying to build a Linux network using older computers, many of which no longer have a working hard disk. Here are the requirements:

[LIST]
[*]All clients are dumb terminals runnning off the Thinstation LiveCD.
[*]All communications between the server and the clients must either be secure or be tunnelled through SSH.
[*]I don't care if I have to start this manually on every boot (these clients aren't supposed to be shut down anyway), but I want something similar to [this]("http://en.wikipedia.org/wiki/File:KDM-Xnest.jpg"), only in fullscreen.
[*]This needs to show a logon screen where users can log in and out as if on a regular desktop. It must be made so that all users must key their usernames, as the server will have too many accounts to just select from a list (not to mention the added security benefit of having to guess usernames as well as passwords).
[*]Upon logon, users must be able to access a GNOME desktop.
[*]Users should not be able to shut down the server from the logon screen.
[*]All profiles must be roaming, but this should already be taken care of considering that the desktop will be running off the server via X11.
[/LIST]
Ideas?

---

