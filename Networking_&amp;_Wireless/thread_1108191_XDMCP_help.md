---
title: "XDMCP help?"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by notrump3 on 2009-03-27
host: hardy - pc
client hardy - laptop

When connecting from the client to the host using Terminal Server Client (xnest installed), it brings up a blank screen with an "X" cursor and freezes.  when window is closed I get the message as attached:

	XIO: fatal IO error 11 (Resource temporarily unavailable) on X server":0.0" 
	after 190 requests (190 known processed) with 0 events remaining

This was working about a month ago, but then began giving this blank screen.

The host was setup through administration->login window with style on remote tab set to "same as local" and on Security tab set "Allow remote system administrator login" enabled, "Never place cookies on NFS" enabled and "only allow login if user owns their home directory" enabled. The permissions is set to "allow login if group write permissions on user's home directory.  I did go to the /etc/gdm/gdm.conf and confirmed the xdmcp is enabled and port=177 is not commented.

As noted above, on the client, xnest is installed and attempted to login either from the login screen ("Remote login through XDMCP") or terminal server client, both result in a blank screen with X cursor. 

ssh is running on the host and I can access through this, but would like to also be able to luach gnome through xdmcp for the the simple stuff.

Not sure if it was an update or something else that stopped it.  The only hardware change was an upgraded router between the units, but there is no firewalling on it between local machines...

Any ideas appreciated

---

