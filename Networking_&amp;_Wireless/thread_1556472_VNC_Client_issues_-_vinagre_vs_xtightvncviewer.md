---
title: "VNC Client issues - vinagre vs xtightvncviewer"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by celem on 2010-08-19
I have XP installed in a Virtualbox. I installed TightVNC server on the virtual-XP with the idea of accessing it from Ubuntu 10.10 AMD64 (or any other machine on my LAN) using the Remote Desktop Viewer (which invokes **vinagre**). When I try to connect I immediately get a dialog box of **CONNECTION CLOSED**. 

I installed **xtightvncviewer**, which if invoked either from the command line or via tsclient connects and works **perfectly**. 

The fact that xtightvncviewer works fine tells me that there is no network connectivity, port or firewall issue and that the problem must lie within vinagre itself.

Are there some sort of issues with vinagre that would prevent it from working to a TightVNC server on Windows?

Any help would be appreciated.

---

### Post by Warped_Dragon on 2010-08-19
I ran in to the same problem, haven't been able to figure it out yet. There is a [bug open (#598597)]("https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/598597") regarding it. In the meantime I've been using xtightvncviewer on it's own.

If you're looking for a gui, in the past I've found [Terminal Server Client]("https://help.ubuntu.com/community/tsclient") to work well with TightVNC, but it's UI irks me enough that I stick to xtightvncviewer.

---

### Post by celem on 2010-08-19
Warped_Dragon - thanks for the heads up on the bug report. I went and voted for it. I am using the Terminal Server Client. It automatically linked to xtightvncviewer for VNC. I have no real problem with using xtightvncviewer except that the login is funky and that vinagre should be working.

---

