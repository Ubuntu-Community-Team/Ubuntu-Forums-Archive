---
title: "Terminal Server Client"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by lenkamholz on 2009-11-21
Hi,

I use VPN to connect to my office win2003 network.  I then use Terminal Server Client to connect to my desktop at work.  This all works great unless the vpn connection gets dropped.  Then  the Terminal Service program hangs, usually when in full screen mode of my work desktop.

I'm new to Ubuntu, so I'm not familiar with how to get out of this gracefully, without leaning on the power switch,  In windows you have ctrl--alt-del, alt-tab, use the task manager to kill a process, etc.  What options do I have?  Especially if it is stuck in full screen mode.

Related Question: If I run the Terminal Services Program in a window instead of full screen, there is no scroll bars!  Whats up with that?  So then I can't see my whole desktop at work in the TS window.  It doesn't scale the work desktop to fit the window.

Len

---

### Post by prshah on 2009-11-21
> **lenkamholz said:**
> I'm not familiar with how to get out of this gracefully, without leaning on the power switch,What options do I have?  Especially if it is stuck in full screen mode.

Related Question: If I run the Terminal Services Program in a window instead of full screen, there is no scroll bars!  

You can use Ctrl+Alt+Enter to toggle between fullscreen and windowed mode.

You can use the "-g" (geometry) switch to specify a workarea size; eg. 1024x768.

Please post back if you want more details.

---

