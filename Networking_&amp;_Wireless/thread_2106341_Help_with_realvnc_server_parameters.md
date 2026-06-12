---
title: "Help with realvnc server parameters"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2013-01-18
I'm testing realvnc, and it works great EXCEPT for some settings in the server I'd like to change.

One connection can connect to a desktop, and then if another connects, it boots the first one off.

I found two settings that will fix it; -NeverShared -DisconnectClients=0

The problem is I've not figured out how to get the server to use these parameters.  

Here is what is running on the system now:

root      1540     1  0 Jan13 ?        00:00:26 vncserver-x11-serviced
root     24919  1540  0 13:51 ?        00:00:00 /usr/bin/vncserver-x11-core -service
mcgadyk  24970     1  0 13:51 ?        00:00:00 /usr/bin/vncserverui service VNC® Server 3
mcgadyk  24988     1  0 13:51 ?        00:00:00 /usr/bin/vncserverui service VNC® Server 3

Notice that vncserver-x11-serviced starts vncserver-x11-core -service, but I need to pass those options to it.

If I manually start this:

/usr/bin/vncserver-x11-core -service -NeverShared -DisconnectClients=0

Then it works perfectly.  When a second client tries to connect, it gives a message that it's already in use.  

I've read the man on these services, but so far I've been unable to have the system start with the -NeverShared -DisconnectClients=0 options.

---

### Post by lisanels47 on 2013-01-23
This is irritating... I've still not been able to find the config files for realVNC server...

---

