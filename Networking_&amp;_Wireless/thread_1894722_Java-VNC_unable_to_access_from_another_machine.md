---
title: "Java-VNC unable to access from another machine"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by bala150985 on 2011-12-13
I have install java-vnc and started VNCserver with the command vncserver :1

Now I have port 6001, 5801 and 5901 listening on my machineA.  When I fireup my browser and hit [http://machineA:5801](http://machineA:5801) I can see that the browser prompts for a password and upon entering that I can see the Gnome interface of Ubuntu. :)

The trouble comes here,  I go to another PC MachineB on the same LAN fireup my browser and hit://machineA:5801

I get the prompt to enter a password after that I get this error

[B]java.net.ConnectException: Connection refused
:confused:

[/B]All my firewalls are disabled.  MachineB has a working Java browser Plugin.

---

