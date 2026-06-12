---
title: "VPN Setup Changes Not Saved in 12.10"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by jlamb70 on 2013-01-22
I have a new install of 12.10 and imported my OpenVPN Connections into the Network Connections. From home, everything worked perfectly. Then I tried to connect from work and it failed. I figure all I need to do is change the port. Should be easy, but it is not.

When I go to the advanced tab to edit the port, I can changed the port and select "ok" This then you returns you to the Network Connections screen where the "Save" button is greyed out. Without saving, the change does not take. 

I next tried just creating a new VPN connection rather than import one. Once again, the "Save" button remained greyed out. At no point during any of this did it ask me to authenticate, which I was expecting and suspect as part of the problem. Has anyone else experienced this or does anyone know what I have missed?

Thanks!

---

### Post by jlamb70 on 2013-01-22
[UPDATE] - all VPN connections now fail (home and work). Somehow what worked on Monday does not work on Tuesday. Sigh.

---

### Post by ahallubuntu on 2013-01-23
I have been using OpenVPN with the Network Manager plug-in for a couple of weeks successfully in 12.04 .  I've had no trouble editing connections.  I am not required to give the admin password to edit my VPN connections, so that isn't the problem.

I can tell you that if you don't have every required field filled out when editing an OpenVPN connection in Network Manager, it will grey out the Save button.  I can also tell you I've had poor luck with importing OpenVPN configuration files with the Network Manager plug-in.  I just added a few new configurations and had to edit each one of them after import despite the fact that all the information was saved in the conf files.

Is there some bug in 12.10 in the Network Manager plug-in, a bug that was introduced after the version used in 12.04?  Could be - but I doubt it.  FYI, my installed version of the OpenVPN Network Manager plug-in is 0.9.4.0-0Ubuntu1 .  You could check to see if you are using that same version; if so, it's very likely not a bug you are seeing.

---

