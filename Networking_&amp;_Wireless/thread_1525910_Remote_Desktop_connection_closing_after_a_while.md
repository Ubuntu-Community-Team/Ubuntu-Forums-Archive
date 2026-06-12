---
title: "Remote Desktop connection closing after a while?"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by BMT22033 on 2010-07-07
Does anyone know what could be causing a Remote Desktop connection to a 10.04 box to be closing after some period of time?  I have three systems all running 10.04 with Remote Desktop enabled.  I'm using UltraVNC on Windows 7 to connect to them.  If I open a connection and leave it open for a long time (like overnight, for example), when I come back in the morning, I still see the VNC window but as soon as I click on it, it closes.  I can immediately open a new connection to the box but it now shows two active connections.  At first I was thinking maybe there's an idle timeout value but given that Ubuntu still seems to think that the original connection is active, maybe the problem isn't on the Ubuntu side but on the UltraVNC side?  Anyone ever experienced this behavior or have any thoughts on what could be causing it?  Thanks!

---

### Post by jwferk on 2010-07-09
[QUOTE=BMT22033;9559093]Does anyone know what could be causing a Remote Desktop connection to a 10.04 box to be closing after some period of time?  I have three systems all running 10.04 with Remote Desktop enabled.  

I'm having a similar problem on 10.  In this case a Ubuntu desktop to a Ubuntu server.  The remote desktop connection works on occasion.  Other times it connects for 1 or 2 seconds and then gives a "connection closed" error message.

Happens in both VNC and SSH mode using either the server name (homeserver.local) or the ip address for the server.

I have gone so far as to disable the firewalls on both machines and still get the same behavior.

---

