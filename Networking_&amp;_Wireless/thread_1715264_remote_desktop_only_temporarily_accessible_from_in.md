---
title: "remote desktop only temporarily accessible from internet"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by raydar on 2011-03-26
I've got an Ubuntu 10.10 machine connected to the Internet via a wireless router which is in turn connected to a cable modem.  I set up remote desktop access through System-->Preferences-->Remote Desktop, with all the checkboxes checked except for "You must confirm each access to this machine."  

For months this setup worked just fine and very reliably; I was always able to control this machine remotely via a VNC connection, except when its dynamic IP address happened to get reset from a power interruption etc.

But recently, the remote desktop has regularly been reverting to > Your desktop is only reachable over the local network. Others can access your computer using the address ____ shortly (as little as 5 or 10 minutes) after being enabled.  When I open the Remote Desktop Preferences as mentioned above, I find all the settings are unchanged, i.e., remote access purportedly enabled.  I discovered that all I need to do in order to re-enable remote access is un-check and then re-check the "Allow other users to view your desktop" checkbox; after a moment, the yellow status box returns to reading > Others can access your computer using the address ____
The only thing "funny" that I can find is that the machine's IP address is never listed among the LAN clients at the bottom of my D-Link router's status page; I don't know whether that was true in previous months when remote desktop access was working constantly without any problems.  The computer's IP address is, however, listed automatically in the Virtual Servers page (where I have external port 80 directed to internal port 5900) and the Port Forwarding page (where I have opened ports 5900,5901,and 3389). Internet access from this machine works fine.

Any advice on how to keep my remote desktop access from becoming unavailable except over the local network except for a few minutes after I disable and then re-enable it?

---

