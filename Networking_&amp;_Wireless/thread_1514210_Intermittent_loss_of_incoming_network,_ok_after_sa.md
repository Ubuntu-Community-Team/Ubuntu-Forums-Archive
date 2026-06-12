---
title: "Intermittent loss of incoming network, ok after safe reboot"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by JayKav on 2010-06-20
Asus M2A-VM AMD athlon X2, 
Lucid 10.04 64 bit

Dual boot Ubuntu/XP running apache, ftp server, remote desktop.

Occasionally, usually immediately following reboot, I have the following:

[LIST]
[*]Unable to access any of the http/ftp/remote-desktop servers from another machine on the network.
[*]Web access from the machine itself is ok. 
[*]Ping works fine (1 or 2 ms response)
[*]IP address and local network address are the same as before
[*]Rebooting into XP everything works fine (I have the same servers running there). 
[*]Normal Ubuntu reboot makes no difference.
[/LIST]

Rebooting into safe mode and then normal mode cures the problem every time.

I can provoke the problem by selecting 'auto configure' in the ubuntu remote desktop dialog.

I'd really like to solve the problem because I want to use the server as an unattended remote server. Any fixes or suggestions to help diagnose it appreciated.

---

