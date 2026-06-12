---
title: "RDP Weirdness"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Warthaug on 2012-01-12
As I mentioned in a previous thread, I need to access a computer here at work over the network for maintenance purposes.  I tried to use VNC over SSH, but due to port blocking by our IT department this was a bust.  So instead I am trying RDP.  This connects very easily, but with one serious problem - instead of getting the "active" desktop on the remote system, I instead appear to get a unique/new desktop environment.  As such I cannot access/manipulate things running on the GUI on the remote machine.  I can, however, see the PIDs of the processes running on the remote machine, and can stop these processes using the kill command.

However, I need access to the "real" desktop; not access to a second desktop.  The remote machine is running lubuntu 11.10, and is running xrdp for the rdp server.  I am accessing via ubuntu 11.04, using terminal server client.

Thanx for any help

Bryan

---

### Post by Warthaug on 2012-01-13
bump

---

