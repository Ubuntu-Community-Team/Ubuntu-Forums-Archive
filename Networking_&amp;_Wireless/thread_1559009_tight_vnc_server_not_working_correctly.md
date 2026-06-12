---
title: "tight vnc server not working correctly"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2010-08-23
64-bit lucid lynx server
According to Ubuntu Software Center, Tight VNC Server is installed. However, 
[LIST=1]
[*]mlocate doesn't show any vnc files in any *bin directory
[*]ps -A doesn't show a vnc service running
[*]none of the menus have an item for vnc server
[/LIST]

I can connect to the ubuntu computer from a Windows vnc client. I can use the keyboard to type in the password. After that, remote control doesn't work.

The problem is that the mouse cursor (controlled from the windows client) moves but otherwise has no effect. I can move the cursor, but it acts as if the client (or server) is set to view-only. The effect of that is that I can't launch any programs (not even a terminal).

I've tried various combinations of settings on the client and on the server, but I can't get it to work correctly.

On the ubuntu machine, remote desktop sharing enabled.

Note: on some earlier versions of ubuntu this worked correctly when connecting from the same windows client using tightvnc.

Update: I tried this using another windows client and got the same results.

---

### Post by snorkytheweasel on 2010-08-23
Because of lack of responses, I cross-posted this to "General" forum.

---

